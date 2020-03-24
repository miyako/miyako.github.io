---
layout: simple
title: COM4Dv3
tags: plugin windows v17
---

A simple inter-process communication tool based on COM.

<!--more-->

[miyako/4d-plugin-com4d-v3](https://github.com/miyako/4d-plugin-com4d-v3/)

4Dのプラグイン（拡張子``.4DX``）は，Windowsのダイナミックライブラリ（拡張子``.DLL``）と基本的に同じものです。通常，DLLには``DllMain``というエントリーポイントがありますが，プラグインの場合，これに加え，``FourDPackex``というエントリーポイントがエクスポートされています。このプラグインは，COM (Component Object Model) オブジェクトのエントリーポイント（下記）をエクスポートすることにより，さまざまな言語（C, C++, C#, Visual Basic, VBScript, JScript）から呼び出せるインタフェースを提供しています。

```def
EXPORTS
    DllCanUnloadNow     PRIVATE
    DllGetClassObject   PRIVATE
    DllRegisterServer   PRIVATE
    DllUnregisterServer PRIVATE
    DllInstall          PRIVATE
    FourDPackex
```

具体的には，``COM4Dv3.Server``という``PROGID``でプラグインをレジストリに登録し，``IDispatch``インタフェースの汎用的なAPI（``Call``というメソッド名）でCOMから呼び出せるようにしています。このメソッドには``1``個以上の``VARIANT``型を渡すことができます。

呼び出し例（C++）：

```cpp
#include <olectl.h>
#include <iostream>
#include <new>
#include <exception>
#include <vector>

#define PROGID_COM4Dv3          L"COM4Dv3.Server"

HRESULT Invoke(IDispatch *pDispatch, LPOLESTR lpszName, WORD wFlags, VARIANT *pVarArray, int nArgs, VARIANT *pVarResult)
{
    DISPPARAMS dispParams;
    DISPID     dispid;
    DISPID     dispidName = DISPID_PROPERTYPUT;
    HRESULT    hr;

    hr = pDispatch->GetIDsOfNames(IID_NULL, &lpszName, 1, LOCALE_USER_DEFAULT, &dispid);
    if (FAILED(hr))
        return hr;

    dispParams.cArgs = nArgs;
    dispParams.rgvarg = pVarArray;
    if (wFlags & DISPATCH_PROPERTYPUT) {
        dispParams.cNamedArgs = 1;
        dispParams.rgdispidNamedArgs = &dispidName;
    }
    else {
        dispParams.cNamedArgs = 0;
        dispParams.rgdispidNamedArgs = NULL;
    }

    hr = pDispatch->Invoke(dispid, IID_NULL, LOCALE_SYSTEM_DEFAULT, wFlags, &dispParams, pVarResult, NULL, NULL);

    return hr;
}

int main(int argc, char*argv[])
{

    IDispatch *pDispatch;

    HRESULT hr = CoInitialize(NULL);

    if (SUCCEEDED(hr)) {

        wchar_t *progid = (wchar_t *)PROGID_COM4Dv3;

        CLSID CLSID_test;
        hr = CLSIDFromProgID(progid, &CLSID_test);

        if (SUCCEEDED(hr)) {

            hr = CoCreateInstance(CLSID_test, NULL, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&pDispatch));
            if (SUCCEEDED(hr)) {

                VARIANT   var[2];
                VARIANT   varResult;

                VariantInit(var);
                VariantInit(&varResult);

                var[0].vt = VT_BSTR;
                var[0].bstrVal = SysAllocString(L"Hello!");

                SYSTEMTIME stime;
                GetSystemTime(&stime);
                DATE today;
                SystemTimeToVariantTime(&stime, &today);

                var[1].vt = VT_DATE;
                var[1].date = today;

                hr = Invoke(pDispatch, L"Call", DISPATCH_METHOD, var, 2, &varResult);

                SysFreeString(var[0].bstrVal);

                VariantClear(var);
                VariantClear(&varResult);

                pDispatch->Release();
            }
            CoUninitialize();
        }
    }
}
```

DLLは，内部的にファイルマップ（``CreateFileMapping``）を使用しており，別々のプロセスや言語でロードされたDLLのインスタンス間でデータをシェアしています。``VARIANT``型で渡された任意の数のパラメーターは，``JSON``オブジェクトの配列（コレクション）``1``個に変換されます。メソッドの呼び出しスタックされ，配列の配列としてファイルマップにバッファリングされます。プラグインがデータを取り出すと，スタックはクリアされます。ファイルマップのサイズは``0x1000000``バイト（``10``MB）に設定されています。

サポートされているバリアント型は，下記のとおりです。

* VT_EMPTY
* VT_NULL
* VT_BSTR
* VT_BOOL
* VT_UI1
* VT_I1
* VT_UI2
* VT_I2
* VT_I4
* VT_UINT
* VT_INT
* VT_R4
* VT_R8
* VT_ERROR
* VT_DATE

下記のバリアント型は，サポートされていません。

* VT_CY
* VT_UI4
* VT_DECIMAL
* VT_BYREF \| \*
* VT_ARRAY
* VT_UNKNOWN
* VT_DISPATCH

プラグインは，オブジェクト型に変換されたパラメーターのコレクションを受け取ります。コレクション内の位置は，渡されたパラメーターの順序に対応します。サポートされていないデータ型は，``null``となります。 ``VT_DATE``は，UTC文字列となります。

例：

```
[
    {
        "type" : "VT_BSTR",
        "value" : "Hello!"
    },
    null,
    {
        "type" : "VT_DATE",
        "value" : "2020-03-21T23:18:44Z"
    }
]

```

---

#### Syntax

```
status:=COM Setup (mode)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">mode</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div> 
</div>

#### COM Setup Modes

Property|Type|Description
------------|------|----
com register|LONGINT|0
com unregister|LONGINT|1
om unregister|LONGINT|2 (default)

プラグインをカレントユーザーのレジストリに登録するには``COM Setup``を使用します。

```
status:=COM Setup (com register)
```

登録状況を調べるには``com get status``を指定します。

```
status:=COM Setup (com get status)
```

レジストリの登録を解除するには``com unregister``を指定します。

```
status:=COM Setup (com unregister)
```

``status``オブジェクトには下記のプロパティが返されます。

* ``clsid``: TEXT 定数（``23B91DD7-EB28-4EE6-809E526F7279516C``）
* ``progid``: TEXT 定数（``COM4Dv3.Server``）
* ``isRegistered``: BOOLEAN （ ``com get status``のみ）

クライアント側は，COMに対応している言語であれば，何でも使用することができます。

---

``COM Write``を使用すれば，4Dをクライアント（またはサーバー兼クライアント）にすることができます。

```
status:=COM Write (params)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">params</div>
  <div class="syntax-td cell cell--2">COLLECTION</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div> 
</div>

コレクションの値は，下記のルールに従って``VARIANT``型に変換されます。

* TEXT: VT_BSTR
* DATE: VT_DATE（日付部のみ。互換性の設定で「オブジェクトではISO日付フォーマットの代わりに日付型を使用する」が有効にされている場合）
* REAL, TIME, LONGINT: VT_R8
* BOOLEAN: VT_BOOL
* NULL: VT_NULL

サポートされていないデータ型は``VT_EMPTY``となります。

書き込みに成功した場合，``status.success``には``True``がセットされ，``status.data``には書き込まれたJSON文字列が返されます。

---

サーバー側は，バッファに溜められたコレクションのコレクションを読むことができます。

```
status:=COM Read
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div> 
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div> 
</div>

``status``オブジェクトには下記のプロパティが返されます。

* ``success``: BOOLEAN 
* ``values``: COLLECTION of COLLECTION of OBJECT
