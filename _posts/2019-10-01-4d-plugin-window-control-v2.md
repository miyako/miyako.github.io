---
layout: simple
title: Window Control
tags: plugin mac userinterface v17
---

Control window icon and button on Mac.

<!--more-->

[miyako/4d-plugin-window-control-v2](https://github.com/miyako/4d-plugin-window-control-v2)

---

```
WINDOW SET ENABLED(window;button;enabled) 
enabled:=WINDOW Get enabled(window;button)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">window</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">button</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">enabled</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div> 
</div>

```
WINDOW SET ICON(window;icon) 
icon:=WINDOW Get enabled(window)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">window</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">button</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">icon</div>
  <div class="syntax-td cell cell--2">PICTURE</div>
  <div class="syntax-td cell cell--8"></div> 
</div>

The ``representedURL`` is set to ``file://`` which corresponds to the system volume path.

#### Window Button Types

Property|Type|Description
------------|------|----
Window close button|LONGINT|
Window minimize button|LONGINT|
Window zoom button|LONGINT|
Window document modified|LONGINT|

#### Added in 2.2.0

```
WINDOW MINIATURIZE(window) 
WINDOW DEMINIATURIZE(window) 
isMiniaturized:=WINDOW Is miniaturized(window)
```
