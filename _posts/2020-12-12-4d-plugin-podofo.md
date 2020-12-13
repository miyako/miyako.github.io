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
location |Text|the message associated with the signature
certification |Text| comma separated list of permissions (optional) valid values are `noPerms`  `formFill`  `annotations`
page |Integer|the page number (1-based) to place the annotation (optional) default is `1`
x |Number|position of the signature annotation (optional)
y |Number|position of the signature annotation (optional)
width |Number|position of the annotation (optional)
height |Number|position of the annotation (optional)
unit |Text|"mm", "in" or "pt" (default)
pages |Collection of Collections|visible annotations
pages[].annotation |Collection of Objects|visible annotations
pages[].text |Collection of Objects|visible text (latin characters only)
certFile |Text|system path to X509 certificate in PEM format; optional if `cert` is passed
cert |Text|certificate in PEM format; optional if `certFile` is passed
keyFile |Text|system path to X509 private key in PEM format; optional if `key` is passed
key |Text|private key in PEM format; optional if `keyFile` is passed
keyPassword |Text|password to open the private key (optional)

#### Annotation

Property|Type|Description
------------|------|----
type | Text|`text` `stamp` `link`
x | Number|
y | Number|
width | Number|
height | Number|
unit | Number| optional
title | Text| optional
open | Boolean| optional
value | Text|for `text` 
icon | Text or Picture|for `stamp` pass the file path or the image itself
URI | Text|for `link` 
color | Object or Number|RGB, CMYK or greyscale
color.r | Number|RGB
color.g | Number|RGB
color.b | Number|RGB
color.c | Number|CMYK
color.m | Number|CMYK
color.y | Number|CMYK
color.k | Number|CMYK

#### Text

Property|Type|Description
------------|------|----
value | Text|
x | Number|
y | Number|
width | Number|
height | Number|
unit | Number| optional
font | Text|optionaloptional
fontSize | Number|optional
halign | Number| `left` (default) `center`  `right`
valign | Number|`top` (default) `bottom` `center`
color | Object or Number|RGB, CMYK or greyscale
color.r | Number|RGB
color.g | Number|RGB
color.b | Number|RGB
color.c | Number|CMYK
color.m | Number|CMYK
color.y | Number|CMYK
color.k | Number|CMYK

#### Status

Property|Type|Description
------------|------|----
error | Integer|`PdfError::GetError()`
errorDescription | Text|`PdfError::errorDescription()`
errorMessage | Text|`PdfError::ErrorMessage`
out | Picture|result PDF (when `params.in` is not passed)

#### Form

```
status:=podofo_get_form(params)
status:=podofo_set_form(params)
```

#### Params (set form)

Property|Type|Description
------------|------|----
in | Picture or Text|PDF content or input system file path
out |Text|output system file path (optional) if omitted, the result is returned in `status.out`
password |Text|password to open the PDF (optional)
rotation |Number|
width |Number|
height |Number|
password |Number|
pages |Collection of Collections|visible annotations
pages[].annotation |Collection of Objects|visible annotations
pages[].text |Collection of Objects|visible text (latin characters only)
pages[].fields |Collection of Objects|fields
keyPassword |Text|password to open the private key (optional)

#### Fields

Property|Type|Description
------------|------|----
type | Text|`textField` `pushButton` `checkBox` `comboBox` `listBox`
fieldName | Text|
x | Number|
y | Number|
width | Number|
height | Number|
unit | Number| optional
isReadOnly | Boolean| 
isRequired | Boolean| 
alternateName | Text| 
highlightingMode | Text| `none` `invert` `invertOutline` `push`
isChecked | Boolean| for `checkBox` 
font | Text|for `textField` 
fontSize | Number|for `textField` 
isPasswordField | Boolean|for `textField` 
isFileField | Boolean|for `textField` 
isScrollBarsEnabled | Boolean|for `textField` 
isCombs | Boolean|for `textField` 
isRichText | Boolean|for `textField` 
isMultiLine | Boolean|for `textField` 
isSpellcheckingEnabled | Boolean|for `textField` 
maxLen | Number|for `textField` 
value | Text|for `textField` 
caption | Text|for `pushButton` `checkBox`
isChecked | Boolean|for `checkBox` 
captions | Object|for `pushButton` 
captions.normal | Object|for `pushButton` 
captions.rollover | Object|for `pushButton` 
captions.alternate | Object|for `pushButton` 
isMultiSelect |Boolean|for `listBox` `comboBox`
isCommitOnSelectionChange |Boolean|for `listBox` `comboBox`
isSorted |Boolean|for `listBox` `comboBox`
 isEditable |Boolean|for `comboBox`
isSpellcheckingEnabled |Boolean|for `listBox` `comboBox`
items |Collection of Objects|for `listBox` `comboBox`
items[].value |Collection of Objects|for `listBox` `comboBox`
items[].displayText |Collection of Objects|for `listBox` `comboBox`
currentItem |Number|for `listBox` `comboBox` 0-based
action |Text|`link` `submit` `reset` `script`
URI |Text|for `link` 
script |Text|for `script` 
events |Collection of Object|
events[].event |Text|`mouseEnter` `mouseLeave` `mouseDown` `mouseUp` `focusEnter` `focusLeave`

#### Remarks 

`annotation.labels[]` does not print non-latin characters (e.g. Japanese). The library API `DrawMultiLineText` does not seem to render glyphs despite FreeType2 linkage.

The signature date is the local timestamp (`PdfDate()`).

TIFF images are not well supported The library API `PdfImage::LoadFromFile`.

>   see https://github.com/svn2github/podofo/blob/master/src/doc/PdfImage.cpp#576

```c
case PHOTOMETRIC_RGB:
if ( bitsPixel != 24 )
{
    TIFFClose(hInTiffHandle);
    PODOFO_RAISE_ERROR( ePdfError_UnsupportedImageFormat );
}
```

Supported annotation types are:

* text
* link
* stamp

#### Other

Great resource: [https://github.com/Universefei/podofomemo](https://github.com/Universefei/podofomemo)
