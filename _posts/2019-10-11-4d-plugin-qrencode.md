---
layout: simple
title: qrencode
tags: plugin graphic v17
---

QR code generator based on [libqrencode](https://fukuchi.org/works/qrencode/).

<!--more-->

[miyako/4d-plugin-qrencode-v2](https://github.com/miyako/4d-plugin-qrencode-v2/)

```
barcode:=qrcode (inData;inParams)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">inData</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">inParams</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">barcode</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>    
</div> 

```
barcodes:=qrcode array (inData;inParams)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">inData</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">inParams</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">barcodes</div>
  <div class="syntax-td cell cell--2">COLLECTION</div>
  <div class="syntax-td cell cell--8"></div>   
</div> 

#### QR Encode Mode

Property|Type|Description
------------|------|----
QR Mode Unicode|LONGINT|0
QR Mode Kanji|LONGINT|1
QR Mode Micro|LONGINT|2
QR Mode Swiss|LONGINT|4

#### QR Error Correction Level

Property|Type|Description
------------|------|----
QR Correction Level L|LONGINT|0
QR Correction Level M|LONGINT|1
QR Correction Level Q|LONGINT|2
QR Correction Level H|LONGINT|3

#### QR Export Type

Property|Type|Description
------------|------|----
QR Format SVG|LONGINT|1
QR Format PNG|LONGINT|2
