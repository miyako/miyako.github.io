---
layout: simple
title: Compact Encoding Detection
tags: plugin text v17
---

Detect text encoding using [CED](https://github.com/google/compact_enc_det).

<!--more-->

[miyako/4d-plugin-compact-enc-det](https://github.com/miyako/4d-plugin-compact-enc-det)

```
status:=CED Detect encoding (data{;params})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">data</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">params</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>    
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>    
</div>

#### Params

Property|Type|Description
------------|------|----
ignore7bitMailEncodings | Boolean|
httpCharsetHint | Text|
metaCharsetHint | Text|
urlHint | Text|
corpus | Text|oen of `WEB_CORPUS` `XML_CORPUS` `QUERY_CORPUS` `EMAIL_CORPUS`

#### Results

Property|Type|Description
------------|------|----
isReliable | Boolean|
bytesConsumed | Number|
encoding | Text|
