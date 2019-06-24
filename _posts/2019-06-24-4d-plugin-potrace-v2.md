---
layout: simple
title: Potrace
tags: plugin graphic v17
---

Rewrite of [Potrace](http://potrace.sourceforge.net) plugin; project based sample DB and ``PROCESS 4D TAGS`` scaffolding.

<!--more-->

[miyako/4d-plugin-potrace-v2](https://github.com/miyako/4d-plugin-potrace-v2)

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
