---
layout: simple
title: Screen Capture
tags: plugin screencapture graphics
---

Screen capture the desktop or a specified window.

<!--more-->

#### Syntax

```
image:=Capture screen ({monitor})
image:=Capture window (window)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">window</div>
<div class="syntax-td cell cell--2">LONGINT</div>
<div class="syntax-td cell cell--8">window reference</div>   
<div class="syntax-td cell cell--2">monitor</div>
<div class="syntax-td cell cell--2">LONGINT</div>
<div class="syntax-td cell cell--8">monitor index (windows only)</div> 
<div class="syntax-td cell cell--2">image</div>
<div class="syntax-td cell cell--2">PICTURE</div>
<div class="syntax-td cell cell--8">captured image</div>   
</div>

* Windows: モニター指定またはSDIモードのウィンドウ指定では[Windows Graphics Capture](https://learn.microsoft.com/en-us/uwp/api/windows.graphics.capture?view=winrt-22621)を使用する

* Mac: [CGWindowListCreateImage](https://developer.apple.com/documentation/coregraphics/1454852-cgwindowlistcreateimage?preferredLanguage=occ)を使用する

### 参考記事

* [Windows の 3 種類のスクリーンキャプチャ API を検証する](https://qiita.com/i_saint/items/ad5b0545873d0cff4604)

* [BitBlt()](): 上に重なっているウィンドウが映ってしまう決定がある。またメインモニターの右または下しか撮影できない。GPUを使用しているWebエリアなどは黒く塗られた領域となる。

* [PrintWindow()](): Windows 8.1で追加された。
