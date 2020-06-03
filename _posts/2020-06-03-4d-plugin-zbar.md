---
layout: simple
title: zbar
tags: plugin graphics v17
---

ひらがな⇄カタカナ・半角⇄全角の変換

<!--more-->

[miyako/4d-plugin-zbar](https://github.com/miyako/4d-plugin-zbar/)

```
result:=ZBAR(image{;types})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">result</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>        
  <div class="syntax-td cell cell--2">types</div>
  <div class="syntax-td cell cell--2">COLLECTION</div>
  <div class="syntax-td cell cell--8"></div>           
</div>

By default, all supported types are considered. Alternatively, you can filter the barcodees types by passing a collection in ``types``.

#### ZBAR Types

Property|Type|Description
------------|------|----
ZBAR_EAN2 | LONGINT| 2
ZBAR_EAN5 | LONGINT|  5
ZBAR_EAN8 | LONGINT| 8
ZBAR_UPCE | LONGINT|  9
ZBAR_ISBN10 | LONGINT|  10
ZBAR_UPCA | LONGINT|  12
ZBAR_EAN13 | LONGINT|  13
ZBAR_ISBN13 | LONGINT|  14
ZBAR_COMPOSITE | LONGINT|  15
ZBAR_I25 | LONGINT|  25
ZBAR_DATABAR | LONGINT|  34
ZBAR_DATABAR_EXPANDED | LONGINT|  35
ZBAR_CODABAR | LONGINT|  38
ZBAR_CODE39 | LONGINT|  39
ZBAR_QRCODE | LONGINT|  64
ZBAR_CODE93 | LONGINT|  93
ZBAR_CODE128 | LONGINT|  128

* PDF417 is disabled because it seems to be unstable.
