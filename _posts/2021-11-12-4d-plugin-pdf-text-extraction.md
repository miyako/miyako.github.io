---
layout: simple
title: pdf-text-extraction
tags: plugin pdf v17
---

PDF text extraction based on [galkahana/pdf-text-extraction](https://github.com/galkahana/pdf-text-extraction).

<!--more-->

[miyako/4d-plugin-pdf-text-extraction](https://github.com/miyako/4d-plugin-pdf-text-extraction/)


#### Digital Signature

```
status:=PDF Text Extraction(path;options)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">path</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>    
  <div class="syntax-td cell cell--2">options</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>      
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>          
</div>

#### Options

Property|Type|Description
------------|------|----
start | Number|
end |Number|
bidi |Text|`LTR` or `RTL`

#### Status

Property|Type|Description
------------|------|----
success | Number|
text |Text|
status |Number|
