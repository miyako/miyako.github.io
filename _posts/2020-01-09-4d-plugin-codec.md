---
layout: simple
title: XML Minify
tags: plugin xml v17
---

Encode or decode data, using [cppcodec](https://github.com/tplgy/cppcodec).

<!--more-->

[miyako/4d-plugin-codec](https://github.com/miyako/4d-plugin-codec/)

```
code:=codec encode (data;codec)
data:=codec decode (code;codec)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">data</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">code</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>    
  <div class="syntax-td cell cell--2">codec</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>      
</div>

#### codec

Property|Type|Description
------------|------|----
base64_rfc4648|LONGINT|
base64_url|LONGINT|
base64_url_unpadded|LONGINT|2
base32_rfc4648|LONGINT|3
base32_crockford|LONGINT|4
base32_hex|LONGINT|5
hex_upper|LONGINT|6
hex_lower|LONGINT|7
