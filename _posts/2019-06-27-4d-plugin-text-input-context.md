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







