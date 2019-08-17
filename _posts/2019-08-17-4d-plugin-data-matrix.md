---
layout: simple
title: DMTX
tags: plugin graphic v17
---

Barcode generator based on [libdmtx](https://github.com/dmtx/libdmtx).

<!--more-->

[miyako/4d-plugin-data-matrix](https://github.com/miyako/4d-plugin-data-matrix)

---

* サンプルプログラムは，プロジェクトモードで開いてください。（17r5以降）

* オブジェクト型を使用しています。（v17以降）

* スレッドセーフです。

**Attention** ``DMTX Read image`` and ``DMTX Read images`` are **thread-unsafe** on Windows 7 due to the use of [SHCreateMemStream](https://docs.microsoft.com/en-us/windows/win32/api/shlwapi/nf-shlwapi-shcreatememstream).

```
barcode:=DMTX (value;format;scheme;module;symbol;margin;dpi;output)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">format</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">scheme</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">module</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">size</div>  
  <div class="syntax-td cell cell--2">symbol</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">size</div>    
  <div class="syntax-td cell cell--2">margin</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">size</div>   
  <div class="syntax-td cell cell--2">dpi</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">output</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">result text</div> 
  <div class="syntax-td cell cell--2">barcode</div>
  <div class="syntax-td cell cell--2">PICTURE</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

```
value:=DMTX Read image (barcode)
values:=DMTX Read images (barcode)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">PICTURE</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">values</div>
  <div class="syntax-td cell cell--2">COLLECTION</div>
  <div class="syntax-td cell cell--8"></div>     
</div>

#### DMTX Scheme

Property|Type|Description
------------|------|----
DMTX Scheme ASCII|LONGINT|
DMTX Scheme C40|LONGINT|
DMTX Scheme Text|LONGINT|
DMTX Scheme X12|LONGINT|
DMTX Scheme Edifact|LONGINT|
DMTX Scheme Base256|LONGINT|

#### DMTX Scheme

Property|Type|Description
------------|------|----
DMTX Format JPG|LONGINT|
DMTX Format SVG|LONGINT|
DMTX Format PNG|LONGINT|

#### DMTX Symbol Size

Property|Type|Description
------------|------|----
DMTX Symbol 10x10|LONGINT|
DMTX Symbol 12x12|LONGINT|
DMTX Symbol 14x14|LONGINT|
DMTX Symbol 16x16|LONGINT|
DMTX Symbol 18x18|LONGINT|
DMTX Symbol 20x20|LONGINT|
DMTX Symbol 22x22|LONGINT|
DMTX Symbol 24x24|LONGINT|
DMTX Symbol 26x26|LONGINT|
DMTX Symbol 32x32|LONGINT|
DMTX Symbol 36x36|LONGINT|
DMTX Symbol 40x40|LONGINT|
DMTX Symbol 44x44|LONGINT|
DMTX Symbol 48x48|LONGINT|
DMTX Symbol 52x52|LONGINT|
DMTX Symbol 64x64|LONGINT|
DMTX Symbol 72x72|LONGINT|
DMTX Symbol 80x80|LONGINT|
DMTX Symbol 88x88|LONGINT|
DMTX Symbol 96x96|LONGINT|
DMTX Symbol 104x104|LONGINT|
DMTX Symbol 120x120|LONGINT|
DMTX Symbol 132x132|LONGINT|
DMTX Symbol 144x144|LONGINT|
DMTX Symbol 8x18|LONGINT|
DMTX Symbol 8x32|LONGINT|
DMTX Symbol 12x26|LONGINT|
DMTX Symbol 12x36|LONGINT|
DMTX Symbol 16x36|LONGINT|
DMTX Symbol 16x48|LONGINT|
