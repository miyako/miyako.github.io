---
layout: simple
title: pngcrush
tags: plugin graphic v17
---

Reduce image size using [pngcrush](http://pmt.sourceforge.net/pngcrush/).

<!--more-->

[miyako/4d-plugin-pngcrush](https://github.com/miyako/4d-plugin-pngcrush/)

```
out:=Pngcrush (in{;chunk})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">in</div>
  <div class="syntax-td cell cell--2">PICTURE</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">out</div>
  <div class="syntax-td cell cell--2">PICTURE</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">chunk</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>    
</div> 

#### Pngcrush options

Property|Type|Description
------------|------|----
PNG_REMOVE_PLTE | LONGINT| 1
PNG_REMOVE_BKGD | LONGINT|  2
PNG_REMOVE_CHRM | LONGINT| 4
PNG_REMOVE_DSIG | LONGINT| 8
PNG_REMOVE_GAMA | LONGINT| 16
PNG_REMOVE_GIFG | LONGINT| 32
PNG_REMOVE_GIFT | LONGINT| 64
PNG_REMOVE_GIFX | LONGINT| 128
PNG_REMOVE_HIST | LONGINT| 256
PNG_REMOVE_ICCP | LONGINT| 512
PNG_REMOVE_ITXT | LONGINT| 1024
PNG_REMOVE_OFFS | LONGINT| 2048
PNG_REMOVE_PHYS | LONGINT| 4096
PNG_REMOVE_PCAL | LONGINT| 8192
PNG_REMOVE_SBIT | LONGINT| 16384
PNG_REMOVE_SCAL | LONGINT| 32768
PNG_REMOVE_SRGB | LONGINT| 65536
PNG_REMOVE_STER | LONGINT| 131072
PNG_REMOVE_SPLT | LONGINT| 262144
PNG_REMOVE_TEXT | LONGINT| 524288
PNG_REMOVE_TIME | LONGINT| 1048576
PNG_REMOVE_TRNS | LONGINT| 2097152
PNG_REMOVE_ZTXT | LONGINT| 4194304
