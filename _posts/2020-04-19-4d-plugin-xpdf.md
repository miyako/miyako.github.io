---
layout: simple
title: Xpdf
tags: plugin pdf v17
---

PDF tools based on [Xpdf](https://www.xpdfreader.com/opensource.html).

<!--more-->

[miyako/4d-plugin-xpdf](https://github.com/miyako/4d-plugin-xpdf/)

```
status:=XPDF_Get_text(path{;params})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">path</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>        
  <div class="syntax-td cell cell--2">params</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>      
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>          
</div>

If ``status.success`` is ``true``, the result is returned in ``status.text``.
