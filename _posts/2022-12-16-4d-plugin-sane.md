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
