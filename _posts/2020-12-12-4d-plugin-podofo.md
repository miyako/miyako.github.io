---
layout: simple
title: podofo
tags: plugin pdf v17
---

PDF tools based on [podofo 0.9.6](http://podofo.sourceforge.net).

<!--more-->

[miyako/4d-plugin-podofo](https://github.com/miyako/4d-plugin-podofo/)

### Features 

* sign PDF
* read and write PDF form values (text field, push button, checkbox)

#### Digital Signature

```
status:=podofo_sign_document(params)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">params</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>      
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>          
</div>

#### Param

property|type|description
------------|------|----
in | Picture or Text|PDF content or input system file path
out |Text|output system file path (optional) if omitted, the result is returned in `status.out`
password |Text|password to open the PDF (optional)
field |Text|field name for the signature; default is "PodofoSignatureField%"
replace |Boolean|whether to update existing fields; default = false
reason |Text|the message associated with the signature
page |Integer|the page number (1-based) to place the annotation (optional)
annotation |Object|parameters for the annotation (optional) annotation is invisible by default
annotation.x |Number|position of the signature annotation
annotation.y |Number|position of the signature annotation
annotation.width |Number|position of the annotation
annotation.height |Number|position of the annotation
annotation.unit |Text|"mm", "in" or "pt" (default)
annotation.images |Collection of Text|paths to use as annotation images (optional)
annotation.images[].path|Text|system path to image file of annotation content
annotation.images[].x|Number|position of the annotation
annotation.images[].y|Number|position of the annotation
annotation.images[].width|Number|position of the annotation
annotation.images[].height|Number|position of the annotation
annotation.images[].unit|Text|"mm", "in" or "pt" (default)
annotation.labels |Collection of Text|text to use as annotation labels (optional)
annotation.labels[].text|Text|annotation content
annotation.labels[].x|Number|position of the annotation
annotation.labels[].y|Number|position of the annotation
annotation.labels[].width|Number|position of the annotation
annotation.labels[].height|Number|position of the annotation
annotation.labels[].unit|Text|"mm", "in" or "pt" (default)
certFile |Text|system path to X509 certificate in PEM format
cert |Text|certificate in PEM format
keyFile |Text|system path to X509 private key in PEM format
key |Text|private key in PEM format

#### Status

property|type|description
------------|------|----
error | Integer|`PdfError::GetError()`
errorDescription | Text|`PdfError::errorDescription()`
errorMessage | Text|`PdfError::ErrorMessage`
out | Picture|result PDF (when `param.in` is not passed)
