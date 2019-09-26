---
layout: simple
title: TWAIN
tags: plugin graphic v17
---

Image scanner based on [twain-dsm](https://github.com/twain/twain-dsm).

<!--more-->

[miyako/4d-plugin-twain-v2](https://github.com/miyako/4d-plugin-twain-v2)

#### Discussion

[Not many scanners have a 64-bit TWAIN driver](https://answers.microsoft.com/en-us/windows/forum/windows_8-hardware/twain-and-64-bit-os/e9910f04-09c3-4f09-a721-2ddd9bd2c257).

[Fujitsu](https://www.fujitsu.com/global/support/products/computing/peripheral/scanners/fi/software/fi6x30-fi6x40-ps-ip-twain64.html)

[Canon](https://cweb.canon.jp/drv-upd/sfs/sc68-win-lide220-103-ea333.html) plug-and-play

[Panasonic](https://panasonic.net/cns/pcc/support/scanner/download.html)

[Ricoh](https://www.ricoh.co.jp/support/os/edition/twain.html) N/A

[hp](https://support.hp.com/ie-en/document/c04635830) N/A

---

```
devices:=TWAIN Get devices
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">devices</div>
  <div class="syntax-td cell cell--2">COLLECTION</div>
  <div class="syntax-td cell cell--8"></div>   
</div>

```
option:=TWAIN Get default option(device.productName)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">device.productName</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">option</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>   
</div>

```
images:=TWAIN Scan(device.productName;option;imageType)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">device.productName</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">option</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">imageType</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">images</div>
  <div class="syntax-td cell cell--2">COLLECTION</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

#### TWAIN image types

Property|Type|Description
------------|------|----
Scanner image type JPEG|LONGINT|
Scanner image type PNG|LONGINT|


