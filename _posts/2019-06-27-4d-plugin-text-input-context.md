---
layout: simple
title: Text Input Context 
tags: plugin userinterface japanese v17
---

Manage text input source on macOS using [NSTextInputContext](https://developer.apple.com/documentation/appkit/nstextinputcontext?language=objc).

[miyako/4d-plugin-text-input-service](https://github.com/miyako/4d-plugin-text-input-service)

<!--more-->

---

```
SET INPUT SOURCE (source)
```

<div class="grid">
  <div class="syntax-th cell cell--3">Parameter</div>
  <div class="syntax-th cell cell--1">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--3">source</div>
  <div class="syntax-td cell cell--1">TEXT</div>
  <div class="syntax-td cell cell--8">Text input source identifier</div>  
</div>

Pass a ``NSTextInputSourceIdentifier`` e.g. ``com.apple.keylayout.US`` to ``source``.

```
GET INPUT SOURCE LOCALES (locales)
```

<div class="grid">
  <div class="syntax-th cell cell--3">Parameter</div>
  <div class="syntax-th cell cell--1">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--3">locales</div>
  <div class="syntax-td cell cell--1">ARRAY TEXT</div>
  <div class="syntax-td cell cell--8">Input sources locale identifier</div>  
</div>

``ALL ROMAN INPUT SOURCES`` is returned for ``NSAllRomanInputSourcesLocaleIdentifier``.

```
SET INPUT SOURCE LOCALES (locales)
```

Parameter|Type|Description
------------|------|----
locales|ARRAY TEXT|``ALL ROMAN INPUT SOURCES`` for ``NSAllRomanInputSourcesLocaleIdentifier``

```
INPUT SOURCES LIST (sources)
```

Parameter|Type|Description
------------|------|----
sources|COLLECTION|

```
_o_INPUT SOURCES LIST (sources)
```

Parameter|Type|Description
------------|------|----
sources|ARRAY TEXT|

```
source:=Get input source
```

Parameter|Type|Description
------------|------|----
source|OBJECT|

```
source:=_o_Get input source
```

Parameter|Type|Description
------------|------|----
source|TEXT|







