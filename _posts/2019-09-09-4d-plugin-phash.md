---
layout: simple
title: pHash
tags: plugin graphic v17
---

Image hash based on [pHash](http://www.phash.org/).

<!--more-->

[miyako/4d-plugin-phash](https://github.com/miyako/4d-plugin-phash)

**Attention** If you create the PNG on Mac OS, make sure the "simple file" option is NOT used. Otherwise the hash value will be zero.

#### Compatibility note

Due to library update (``0.9.6`` to ``1.0.0``), function results are not the same as the old plugin. 

Previous version was using the original ``0.9.6`` code for UNIX/MinGW.

Current version uses ``1.0.0`` for Mac and a pseudo ``1.0.0`` for Windows (based on ``0.9.0`` distributed with ``1.0.0``).

Windows 64-bit uses [``__popcnt64``](https://docs.microsoft.com/en-us/cpp/intrinsics/popcnt16-popcnt-popcnt64). ``__cpuid`` is **not checked**, since 64-bit version of 4D requires SSE4 anyway. 32-bit version uses classic emulation code.

```c
ulong64 x = hash1^hash2;
#ifdef _WIN64
    return __popcnt64(x);
#else
  const ulong64 m1 = 0x5555555555555555ULL;
  const ulong64 m2 = 0x3333333333333333ULL;
  const ulong64 h01 = 0x0101010101010101ULL;
  const ulong64 m4 = 0x0f0f0f0f0f0f0f0fULL;
  x -= (x >> 1) & m1;
  x = (x & m2) + ((x >> 2) & m2);
  x = (x + (x >> 4)) & m4;
 
  return int((x * h01) >> 56);
#endif
```

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
