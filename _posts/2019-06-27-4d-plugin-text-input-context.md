---
layout: Text Input Context 
title: Imebra
tags: plugin userinterface japanese v17
---

Manage text input source on macOS using [NSTextInputContext](https://developer.apple.com/documentation/appkit/nstextinputcontext?language=objc).

[miyako/4d-plugin-text-input-service](https://github.com/miyako/4d-plugin-text-input-service)

<!--more-->

---

```
SET INPUT SOURCE (source)
```

Parameter|Type|Description
------------|------|----
source|TEXT|``NSTextInputSourceIdentifier``

<div class="grid">
  <div class="cell cell--4">Parameter</div>
  <div class="cell cell--2">Type</div>
  <div class="cell cell--6">Description</div>
  <div class="cell cell--4">source</div>
  <div class="cell cell--2">TEXT</div>
  <div class="cell cell--6">``NSTextInputSourceIdentifier``</div>
</div>

```
GET INPUT SOURCE LOCALES (locales)
```

Parameter|Type|Description
------------|------|----
locales|ARRAY TEXT|``ALL ROMAN INPUT SOURCES`` for ``NSAllRomanInputSourcesLocaleIdentifier``

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







