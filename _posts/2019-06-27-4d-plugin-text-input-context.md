---
layout: simple
title: Text Input Context 
tags: plugin userinterface japanese v17
---

Manage text input source on macOS using [NSTextInputContext](https://developer.apple.com/documentation/appkit/nstextinputcontext?language=objc).

<!--more-->

[miyako/4d-plugin-text-input-context](https://github.com/miyako/4d-plugin-text-input-context)

---

* サンプルプログラムは，プロジェクトモードで開いてください。（17r5以降）

* オブジェクト型やコレクション型を使用しています。（v17以降）

* スレッドセーフです。

* v16以前で使用する場合，Releasesから``1.0``版をダウンロードしてください。

* ``-carbon``とタグ付けされているリリースは，32/64ビット対応です。

```
SET INPUT SOURCE (source)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">source</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">Text input source identifier</div>  
</div>

Pass an ``NSTextInputSourceIdentifier`` e.g. ``com.apple.keylayout.US`` to ``source``.

入力ソースを切り替えます。ソースの識別子は，``_o_INPUT SOURCES LIST`` ``_o_Get input source``などから返される文字列です。

例：

``com.apple.inputmethod.Kotoeri.Japanese``  
``jp.co.ergo.egbridge_universal_2.component.Japanese``  
``com.justsystems.inputmethod.atok22.Japanese``  
``com.google.inputmethod.Japanese.base``

```
GET INPUT SOURCE LOCALES (locales)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">locales</div>
  <div class="syntax-td cell cell--2">ARRAY TEXT</div>
  <div class="syntax-td cell cell--8">Input sources locale identifier</div>  
</div>

``ALL ROMAN INPUT SOURCES`` is returned for ``NSAllRomanInputSourcesLocaleIdentifier``.

カレントの入力ソースが対応しているロケールのリストが返されます。デフォルトは空の配列です。

```
SET INPUT SOURCE LOCALES (locales)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">locales</div>
  <div class="syntax-td cell cell--2">ARRAY TEXT</div>
  <div class="syntax-td cell cell--8">Text input source locales</div>  
</div>

Pass ``ALL ROMAN INPUT SOURCES`` to specify ``NSAllRomanInputSourcesLocaleIdentifier``.

Pass an empty array to allow any locale.

ロケールは，一般的な言語コードで指定します。英数一般は``ALL ROMAN INPUT SOURCES``定数で指定することができます。空の配列を渡した場合，ロケールの制限はありません。英数モードから復帰する場合，他の言語が制限されたままにならないよう，日本語（``ja``）ではなく，空の配列を渡すようにしてください。

```
sources:=Input sources list
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">sources</div>
  <div class="syntax-td cell cell--2">COLLECTION</div>
  <div class="syntax-td cell cell--8">Text input sources</div>  
</div>

Returns a collection of objects that contains information about keyboard text input sources.

#### Text input source

Property|Type|Description
------------|------|----
source|OBJECT|
source.id|TEXT|
source.name|TEXT|``localizedNameForInputSource``

```
_o_INPUT SOURCES LIST (sources)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">sources</div>
  <div class="syntax-td cell cell--2">ARRAY TEXT</div>
  <div class="syntax-td cell cell--8">Text input source identifiers</div>  
</div>

Simply returns an array of identifier string ([``selectedKeyboardInputSource``](https://developer.apple.com/documentation/appkit/nstextinputcontext/1533970-selectedkeyboardinputsource?language=objc)) of keyboard text input sources.

```
source:=Get input source
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">source</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8">Text input source</div>  
</div>

Returns an object that contains information about the currently selected keyboard text input source.

#### Text input source

Property|Type|Description
------------|------|----
source|OBJECT|
source.id|TEXT|
source.name|TEXT|``localizedNameForInputSource``
source.category|TEXT|``kTISPropertyInputSourceCategory``
source.type|TEXT|``kTISPropertyInputSourceType``
source.icon|PICTURE|``kTISPropertyIconRef`` or content of ``kTISPropertyIconImageURL``
source.languages\[\]|COLLECTION|``kTISPropertyInputSourceLanguages``

```
source:=_o_Get input source
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">source</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">Text input source identifier</div>  
</div>

Simply returns the identifier string ([``selectedKeyboardInputSource``](https://developer.apple.com/documentation/appkit/nstextinputcontext/1533970-selectedkeyboardinputsource?language=objc)) for the currently selected keyboard text input source.
