---
layout: simple
title: Input Scope
tags: plugin text windows userinterface v17
---

Simple wrapper for [SetInputScope](https://docs.microsoft.com/ja-jp/windows/win32/api/inputscope/nf-inputscope-setinputscope).

<!--more-->

[miyako/4d-plugin-input-scope](https://github.com/miyako/4d-plugin-input-scope)

```
status:=Set input scope (scope)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">scope</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">InputScope Enumeration</div>  
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>      
</div>

#### Options

[InputScope Enumeration](https://docs.microsoft.com/en-us/windows/win32/api/inputscope/ne-inputscope-inputscope)の定数をそのまま渡すことができます。
