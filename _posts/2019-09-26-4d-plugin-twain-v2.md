---
layout: simple
title: TWAIN
tags: plugin graphic v17
---

Image scanner based on [twain-dsm](https://github.com/twain/twain-dsm).

<!--more-->

[miyako/4d-plugin-twain-v2](https://github.com/miyako/4d-plugin-twain-v2)

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
TWAIN SCAN(device.productName;option;imageType;images)
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
  <div class="syntax-td cell cell--2">ARRAY PICTURE</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

#### TWAIN image types

Property|Type|Description
------------|------|----
Scanner image type JPEG|LONGINT|
Scanner image type PNG|LONGINT|


