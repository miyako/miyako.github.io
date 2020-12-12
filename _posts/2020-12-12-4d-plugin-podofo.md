---
layout: simple
title: podofo
tags: plugin pdf v17
---

PDF tools based on [podofo 0.9.6](http://podofo.sourceforge.net).

<!--more-->

[miyako/4d-plugin-podofo](https://github.com/miyako/4d-plugin-podofo/)

### Features 

* add signature to existing PDF document
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

#### Params

Property|Type|Description
------------|------|----
in | Picture or Text|PDF content or input system file path
out |Text|output system file path (optional) if omitted, the result is returned in `status.out`
password |Text|password to open the PDF (optional)
field |Text|field name for the signature; default is "PodofoSignatureField%" where `%` is the object number
replace |Boolean|whether to update existing fields; default = false; if passed, the specified `field` should be of a signature field type
reason |Text|the message associated with the signature
page |Integer|the page number (1-based) to place the annotation (optional) default is `1`
x |Number|position of the signature annotation
y |Number|position of the signature annotation
width |Number|position of the annotation
height |Number|position of the annotation
unit |Text|"mm", "in" or "pt" (default)
pages |Collection of Collections|visible annotations
pages[].annotation |Collection of Objects|visible annotations
certFile |Text|system path to X509 certificate in PEM format; optional if `cert` is passed
cert |Text|certificate in PEM format; optional if `certFile` is passed
keyFile |Text|system path to X509 private key in PEM format; optional if `key` is passed
key |Text|private key in PEM format; optional if `keyFile` is passed
keyPassword |Text|password to open the private key (optional)

#### Status

Property|Type|Description
------------|------|----
error | Integer|`PdfError::GetError()`
errorDescription | Text|`PdfError::errorDescription()`
errorMessage | Text|`PdfError::ErrorMessage`
out | Picture|result PDF (when `params.in` is not passed)

#### Remarks 

`annotation.labels[]` does not print non-latin characters (e.g. Japanese). The library API `DrawMultiLineText` does not seem to render glyphs despite FreeType2 linkage.

The signature date is the local timestamp (`PdfDate()`).


