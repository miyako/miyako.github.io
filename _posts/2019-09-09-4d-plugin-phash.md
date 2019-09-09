---
layout: simple
title: pHash
tags: plugin graphic v17
---

Image hash based on [pHash](http://www.phash.org/).

<!--more-->

[miyako/4d-plugin-phash](https://github.com/miyako/4d-plugin-phash)

**Attention** If you create the PNG on Mac OS, make sure the "simple file" option is NOT used. Otherwise the hash value will be zero.

#### Library version

Mac: pHash ``1.0.0`` gives slightly different results compared to the original pHash ``0.9.6``.

Windows: pHash for Windows `0.9.0` (distributed with ``1.0.0``) gives similar results as the original pHash ``0.9.6`` (MinGW DLL), except for ``PH Compare MH``.

---

```
status:=PH Compute DCT(file;hash)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">file</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">hash</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div> 
</div>  

wrapper of ``ph_dct_imagehash``. 

**Attention** contrary to header file description, status is ``0`` (not ``1``) for success and ``-1`` for failure.

```
pcc:=PH Compare RADISH(file1;file2;sigma;gamma;n)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">file1</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">file2</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">sigma</div>
  <div class="syntax-td cell cell--2">REAL</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">gamma</div>
  <div class="syntax-td cell cell--2">REAL</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">n</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">pcc</div>
  <div class="syntax-td cell cell--2">REAL</div>
  <div class="syntax-td cell cell--8"></div>  
</div> 

wrapper of ``ph_crosscorr``. 

```
pcc:=PH Compare MH(file1;file2;alpha;lvl)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">file1</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">file2</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">alpha</div>
  <div class="syntax-td cell cell--2">REAL</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">lvl</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">pcc</div>
  <div class="syntax-td cell cell--2">REAL</div>
  <div class="syntax-td cell cell--8"></div>  
</div> 

wrapper of ``ph_hammingdistance2``. 

```
distance:=PH Compare DCT(hash1;hash2)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">hash1</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">hash2</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">distance</div>
  <div class="syntax-td cell cell--2">REAL</div>
  <div class="syntax-td cell cell--8"></div>   
</div> 
