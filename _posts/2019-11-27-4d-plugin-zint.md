---
layout: simple
title: zint
tags: plugin graphic v17
---

Barcode generator based on [zint](https://zint.github.io/).

<!--more-->

[miyako/4d-plugin-zint-v2](https://github.com/miyako/4d-plugin-zint-v2/)

```
barcode:=zint (inData;inParams)
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

#### Parameters

Property|Type|Description
------------|------|----
ZINT_HEIGHT|LONGINT|
ZINT_TYPE|LONGINT|
ZINT_FORMAT|LONGINT|
ZINT_WHITE_SPACE|LONGINT|
ZINT_BORDER|LONGINT|
ZINT_BOX|BOOLEAN|
ZINT_BIND|BOOLEAN|
ZINT_SCALE|REAL|
ZINT_ROTATE|LONGINT|``90`` ``180`` ``270`` ``0``
ZINT_COLUMNS|LONGINT|
ZINT_VERSION|LONGINT|
ZINT_SECURE|LONGINT|
ZINT_PRIMARY|TEXT|
ZINT_MODE|LONGINT|
ZINT_GS1|BOOLEAN|
ZINT_NO_TEXT|BOOLEAN|
ZINT_SQUARE|BOOLEAN|
ZINT_KANJI|BOOLEAN|
ZINT_SJIS|BOOLEAN|
ZINT_SMALL_TEXT|BOOLEAN|
ZINT_DPI|LONGINT|
ZINT_NO_BACKGROUND|BOOLEAN|
