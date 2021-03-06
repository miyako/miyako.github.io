---
layout: simple
title: Native Encoding Detection
tags: plugin text v17
---

Detect text encoding of BLOB.

<!--more-->

[miyako/4d-plugin-native-encoding-detection](https://github.com/miyako/4d-plugin-native-encoding-detection/)

```
status:=NED Detect encoding(data{;params})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">data</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8">source text</div>      
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
sourceTextType | Text|one of `7bit` `8bit` `dbcs` `html` Windows only
preferredCodePage | Number|Windows only 

#### Results

Property|Type|Description
------------|------|----
encodings[].code | Number|can be `-1` on Mac (`kCFStringEncodingInvalidId`)
encodings[].language | Text|platform specific identifier; can be `-1` on Windows
encodings[].charset | Text|IANA charset name
encodings[].name | Text|platform specific identifier
encodings[].script | Text|Mac only
encodings[].percentage | Number|Windows only
encodings[].confidence | Number|Windows only
encodings[].fixedWidthFont | Text|Windows only
encodings[].proportionalFont | Text|Windows only
