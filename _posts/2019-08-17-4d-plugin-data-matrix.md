---
layout: simple
title: DMTX
tags: plugin graphics v17
---

Barcode generator based on [libdmtx](https://github.com/dmtx/libdmtx).

<!--more-->

[miyako/4d-plugin-data-matrix](https://github.com/miyako/4d-plugin-data-matrix)

---

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
value:=DMTX Read image (barcode;values)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">PICTURE</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">values</div>
  <div class="syntax-td cell cell--2">TEXT ARRAY</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>    
</div>
