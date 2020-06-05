---
layout: simple
title: MDI
tags: plugin userinterface windows v17
---

Resize the MDI window.

<!--more-->

[miyako/4d-plugin-mdi](https://github.com/miyako/4d-plugin-mdi/)

```
MDI SET TITLE (title)
title:=MDI Get title
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">title</div>
  <div class="syntax-td cell cell--2">TEXT</div>           
</div>

```
MDI MAXIMIZE
MDI MINIMIZE
MDI RESTORE
```

```
MDI SET CLOSE BOX ENABLED(enabled)
enabled:=MDI Get close box enabled
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">enabled</div>
  <div class="syntax-td cell cell--2">LONGINT</div>           
</div>

```
MDI USE ICON FILE(iconPath)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">iconPath</div>
  <div class="syntax-td cell cell--2">TEXT</div>           
</div>

```
MDI GET POSITION(left;top;width;height)
MDI SET POSITION(positioning;left;top;width;height;zOrder)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">left</div>
  <div class="syntax-td cell cell--2">LONGINT</div>  
  <div class="syntax-td cell cell--2">top</div>
  <div class="syntax-td cell cell--2">LONGINT</div>  
  <div class="syntax-td cell cell--2">width</div>
  <div class="syntax-td cell cell--2">LONGINT</div>  
  <div class="syntax-td cell cell--2">height</div>
  <div class="syntax-td cell cell--2">LONGINT</div>  
  <div class="syntax-td cell cell--2">positioning</div>
  <div class="syntax-td cell cell--2">LONGINT</div>  
  <div class="syntax-td cell cell--2">zOrder</div>
  <div class="syntax-td cell cell--2">LONGINT</div>    
</div>


#### Window Z-Order Flags

Property|Type|Description
------------|------|----
HWND_BOTTOM | LONGINT| 1
HWND_NOTOPMOST | LONGINT|  -2
HWND_TOP | LONGINT| 0
HWND_TOPMOST | LONGINT|  -1

#### Window Position Flags

SWP_ASYNCWINDOWPOS | LONGINT|  16384
SWP_DEFERERASE | LONGINT|  8192
SWP_DRAWFRAME | LONGINT|  32
SWP_HIDEWINDOW | LONGINT|  128
SWP_NOACTIVATE | LONGINT|  16
SWP_NOCOPYBITS | LONGINT|  256
SWP_NOMOVE | LONGINT|  2
SWP_NOOWNERZORDER | LONGINT|  512
SWP_NOREDRAW | LONGINT|  8
SWP_NOSENDCHANGING | LONGINT|  1024
SWP_NOSIZE | LONGINT|  1
SWP_NOZORDER | LONGINT|  4
SWP_SHOWWINDOW | LONGINT|  64
