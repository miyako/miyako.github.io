---
layout: simple
title: SANE
tags: plugin scanner
---

Decode QR code with OpenCV.

<!--more-->

SANE ([Scanner Access Now Easy](http://www.sane-project.org)) for macOS

#### Syntax

```
scanners:=SANE Scanners list(names)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">scanners</div>
<div class="syntax-td cell cell--2">COLLECTION</div>
<div class="syntax-td cell cell--8">collection of scanner objects</div>   
<div class="syntax-td cell cell--2">names</div>
<div class="syntax-td cell cell--2">ARRAY TEXT</div>
<div class="syntax-td cell cell--8">array of scanner names, JSON summary in element 0</div>   
</div>

Property|Type|Description
------------|------|----
scanner | Object|
scanner.name | Text|
scanner.vendor | Text|
scanner.model | Text|
scanner.type | Text|

```
images:=SANE Scan(scannerName; type)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">images</div>
<div class="syntax-td cell cell--2">COLLECTION</div>
<div class="syntax-td cell cell--8">collection of images</div>  
<div class="syntax-td cell cell--2">scannerName</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8"></div>   
<div class="syntax-td cell cell--2">type</div>
<div class="syntax-td cell cell--2">LONGINT</div>
<div class="syntax-td cell cell--8">`image_type_jpg(0)` or `image_type_png(0)`</div>  
</div>

```
options:=SANE Scan option values(scannerName; optionValues)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">scannerName</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8"></div> 
<div class="syntax-td cell cell--2">optionValues</div>
<div class="syntax-td cell cell--2">ARRAY TEXT</div>
<div class="syntax-td cell cell--8">array of option values, JSON summary in element 0</div>   
<div class="syntax-td cell cell--2">options</div>
<div class="syntax-td cell cell--2">COLLECTION</div>
<div class="syntax-td cell cell--8"></div>
</div>

```
SANE SET SCAN OPTION(scannerName; optionName; optionValue)
optionValue:=SANE Get scan option(scannerName; optionName)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">scannerName</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8"></div> 
<div class="syntax-td cell cell--2">optionName</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8"></div>   
<div class="syntax-td cell cell--2">optionValue</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8"></div>   
</div>
