---
layout: simple
title: qrencode
tags: plugin graphic v17
---

QR code generator based on [libqrencode 4.0.0](https://fukuchi.org/works/qrencode/).

<!--more-->

[miyako/4d-plugin-qrencode](https://github.com/miyako/4d-plugin-qrencode)

```
barcode:=QRCODE (inData;inOutputFormat;inMode;inErrorCorrectionLevel;inVersion;inSize;inMargin;inDPI;outData)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">inData</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">inOutputFormat</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">inMode</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">inErrorCorrectionLevel</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">inVersion</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">inSize</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">inMargin</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">inDPI</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">outData</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">barcode</div>
  <div class="syntax-td cell cell--2">PICTURE</div>
  <div class="syntax-td cell cell--8"></div>    
</div> 

```
QRCODE ARRAY (inData;inOutputFormat;inMode;inErrorCorrectionLevel;inVersion;inSize;inMargin;inDPI;outData)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">inData</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">inOutputFormat</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">inMode</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">inErrorCorrectionLevel</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">inVersion</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">inSize</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">inMargin</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">inDPI</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">outData</div>
  <div class="syntax-td cell cell--2">ARRAY PICTURE</div>
  <div class="syntax-td cell cell--8"></div>   
</div> 

#### QR Encode Mode

Property|Type|Description
------------|------|----
QR Mode Unicode|LONGINT|
QR Mode Kanji|LONGINT|
QR Mode Micro|LONGINT|
QR Mode Latin|LONGINT|

#### QR Error Correction Level

Property|Type|Description
------------|------|----
QR Correction Level L|LONGINT|
QR Correction Level M|LONGINT|
QR Correction Level Q|LONGINT|
QR Correction Level H|LONGINT|

#### QR Export Type

Property|Type|Description
------------|------|----
QR Format SVG|LONGINT|
QR Format PNG|LONGINT|
