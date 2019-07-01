---
layout: simple
title: Potrace
tags: plugin graphic v17
---

Rewrite of [Potrace](http://potrace.sourceforge.net) plugin; project based sample DB and ``PROCESS 4D TAGS`` scaffolding.

<!--more-->

[miyako/4d-plugin-potrace-v2](https://github.com/miyako/4d-plugin-potrace-v2)

---

* サンプルプログラムは，プロジェクトモードで開いてください。（17r5以降）

* オブジェクト型を使用しています。（v17以降）

* スレッドセーフです。

```
image:=Potrace (data{;options})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">data</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8">BMP image data</div>  
  <div class="syntax-td cell cell--2">options</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">image</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>    
</div>

#### Options

Property|Type|Description
------------|------|----
format|TEXT|``.svg`` ``.pdf``
policy|TEXT|``black`` ``white`` ``right`` ``left`` ``minority`` ``majority`` ``random``
turdsize|LONGINT|
alphamax|REAL|
opticurve|BOOLEAN|
opttolerance|REAL|
opaque|BOOLEAN|
invert|BOOLEAN|
tight|BOOLEAN|
angle|REAL|
gamma|REAL|
blacklevel|REAL|
stretch|REAL|
unit|REAL|
group|TEXT|``flat`` ``connected`` ``hierarchical``
longcoding|BOOLEAN|
fillcolor|TEXT|
color|TEXT|
width|TEXT|
height|TEXT|
pagesize|TEXT|``A4`` ``A3`` ``A5`` ``B5`` ``Letter`` ``Legal`` ``Tabloid`` ``Statement`` ``Executive`` ``Folio`` ``Quarto`` ``10x14``
scale|TEXT|
resolution|TEXT|
bottommargin|TEXT|
topmargin|TEXT|
rightmargin|TEXT|
leftmargin|TEXT|

```
image:=Mkbitmap (data{;options})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">data</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8">BMP image data</div>  
  <div class="syntax-td cell cell--2">options</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">image</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>    
</div>

#### Options

Property|Type|Description
------------|------|----
filter|REAL|
blur|REAL|
scale|REAL|
threshold|REAL|
grey|BOOLEAN|
linear|BOOLEAN|
cubic|BOOLEAN|
nofilter|BOOLEAN|
invert|BOOLEAN|
nodefaults|BOOLEAN|
