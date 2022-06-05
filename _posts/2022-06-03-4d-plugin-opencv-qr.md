---
layout: simple
title: OpenCV QR
tags: plugin barcode
---

Decode QR code with OpenCV.

<!--more-->

[miyako/4d-plugin-opencv-qr](https://github.com/miyako/4d-plugin-opencv-qr)

#### Syntax

```
status:=opencv decode qrcode(image{;epsilon})
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">image</div>
<div class="syntax-td cell cell--2">PICTURE</div>
<div class="syntax-td cell cell--8">image containing QR codes</div>   
<div class="syntax-td cell cell--2">epsilon</div>
<div class="syntax-td cell cell--2">REAL</div>
<div class="syntax-td cell cell--8">epsX, epsY</div>   
<div class="syntax-td cell cell--2">status</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8"></div>   
</div>

Property|Type|Description
------------|------|----
status | Object|
status.success | Boolean|
status.values | Collection of Text|
status.images | Collection of Pictures|
status.corners | Collection of Objects|
