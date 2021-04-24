---
layout: simple
title: Window Style
tags: plugin userinterface mac v19
---

Customise window appearance on Mac; for 4D v19.

<!--more-->

[miyako/4d-plugin-window-style](https://github.com/miyako/4d-plugin-window-style/)

```
SET WINDOW STYLE(window;params)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">window</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>      
  <div class="syntax-td cell cell--2">params</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>         
</div>

#### Params

Property|Type|Description
------------|------|----
opaque | Boolean|`setOpaque:`
titlebarAppearsTransparent | Boolean|`NSWindowStyleMaskFullSizeContentView` `setTitlebarAppearsTransparent:`
movableByWindowBackground | Boolean|`setMovableByWindowBackground:`
backgroundColor | Object|`red` `green` `blue` `alpha`
backgroundImage | Picture|
backgroundImagePath | Text|

#### Discussions

It seems like `setStyleMask:` with the `NSWindowStyleMaskFullSizeContentView` no longer has effect on v19. The content view is always places below the title bar, no under it. 

To remove the title bar design in v19, it is necessary to assign an opaque colour to the window background or else add an image layer.
