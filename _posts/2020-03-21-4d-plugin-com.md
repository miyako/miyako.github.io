---
layout: simple
title: COM4Dv3
tags: plugin windows v17
---

A simple inter-process communication tool based on COM.

<!--more-->

[miyako/4d-plugin-com4d-v3](https://github.com/miyako/4d-plugin-com4d-v3/)

まず，プラグインをカレントユーザーのレジストリに登録します。

```
status:=COM Setup (com register)
```

すでに登録されているか，調べるには``com get status``を指定します。

```
status:=COM Setup (com get status)
```

登録を解除するには``com unregister``を指定します。

```
status:=COM Setup (com unregister)
```

``status``オブジェクトには下記のプロパティが返されます。

* ``clsid``: TEXT 定数（``23B91DD7-EB28-4EE6-809E526F7279516C``）
* ``progid``: TEXT 定数（``COM4Dv3.Server``）
* ``isRegistered``: BOOLEAN （ ``com get status``のみ）

クライアント側は，COMに対応している言語であれば，何でも使用することができます。

4Dをクライアントにする場合，``COM Write``が使用できます。


```
status:=COM Write (json)
```

サーバー側は，バッファに溜められたコレクションのコレクションを読むことができます。

```
status:=COM Read
```

``status``オブジェクトには下記のプロパティが返されます。

* ``success``: BOOLEAN 
* ``values``: COLLECTION of COLLECTION of OBJECT

---

クライアント側は，任意の``VARIANT``型をパラメーターとして渡すことができます。サーバー側（4D）は，オブジェクト型のコレクション（JSON）でパラメーターを受け取ります。要素の番号は，パラメーターの順序に対応します。

* ``VT_DATE``は，UTC文字列となります。

例：

```
SYSTEMTIME param_time;
GetSystemTime(&param_time);

DATE param_date;
SystemTimeToVariantTime(&param_time, &param_date);

var[0].vt = VT_DATE;
var[0].date = param_date;
```

```
{
    "type" : "VT_DATE",
    "value" : "2020-03-21T23:18:44Z"
}
```

対応していないデータ型は，``null``となります。

```
[
    {
        "type" : "VT_BSTR",
        "value" : "Hello World!"
    },
    null,
    {
        "type" : "VT_DATE",
        "value" : "2020-03-21T23:18:44Z"
    }
]

```

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
* VT_BYREF | *
* VT_ARRAY
* VT_UNKNOWN
* VT_DISPATCH
