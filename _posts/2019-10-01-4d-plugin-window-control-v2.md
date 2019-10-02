---
layout: simple
title: Window Control
tags: plugin mac userinterface v17
---

Volume mount notification for Mac.

<!--more-->

[miyako/4d-plugin-mount](https://github.com/miyako/4d-plugin-mount)

---

```
name:=Unmount(path) 
Mount(name) 
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">path</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">system path</div>  
  <div class="syntax-td cell cell--2">name</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">BSD name</div>  
</div>

```
Mount WATCH(method) 
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">method</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

The ``representedURL`` is set to ``file://`` which corresponds to the system volume path.

#### Mount Event Types

Property|Type|Description
------------|------|----
Volume did mount event|LONGINT|
Volume will unmount event|LONGINT|
Volume did unmount event|LONGINT|
Volume did rename event|LONGINT|
