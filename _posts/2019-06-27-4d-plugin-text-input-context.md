---
layout: simple
title: Text Input Context 
tags: plugin userinterface japanese v17
---

Manage text input source on macOS using [NSTextInputContext](https://developer.apple.com/documentation/appkit/nstextinputcontext?language=objc).

<!--more-->

[miyako/4d-plugin-text-input-context](https://github.com/miyako/4d-plugin-text-input-context)

---

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
