---
layout: simple
title: PICTURE TO BLOB without conversion
tags: plugin graphic v17
---

PICTURE TO BLOB without conversion. 

<!--more-->

Perhaps useful to extact PICT data without invoking QuickDraw API.

[miyako/4d-plugin-raw-picture-data](https://github.com/miyako/4d-plugin-raw-picture-data/)

```
GET PICTURE DATA (PICT;arrType;arrData)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">PICT</div>
  <div class="syntax-td cell cell--2">PICTURE</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">arrType</div>
  <div class="syntax-td cell cell--2">ARRAY TEXT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">arrData</div>
  <div class="syntax-td cell cell--2">ARRAY BLOB</div>
  <div class="syntax-td cell cell--8"></div>    
</div> 

```
data:=Get picture data for type (PICT;type)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">PICT</div>
  <div class="syntax-td cell cell--2">PICTURE</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">type</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">data</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>    
</div> 
