---
layout: simple
title: Potrace
tags: plugin graphic v17
---

Rewrite of [Potrace](http://potrace.sourceforge.net) plugin; project based sample DB and ``PROCESS 4D TAGS`` scaffolding.

[miyako/4d-plugin-imebra-v3](https://github.com/miyako/4d-plugin-potrace-v2)

<!--more-->

---

### Syntax

```
image:=Potrace (data{;options})
```

Parameter|Type|Description
------------|------|----
data|BLOB|BMP image data
options|OBJECT|
image|OBJECT|

```
image:=Mkbitmap (data{;options})
```

Parameter|Type|Description
------------|------|----
data|BLOB|BMP image data
options|OBJECT|
image|OBJECT|
