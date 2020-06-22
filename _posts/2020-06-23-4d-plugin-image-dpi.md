---
layout: simple
title: Image DPI
tags: plugin graphics v17
---

画像ファイルの解像度情報を書き換え

<!--more-->

[miyako/4d-plugin-image-dpi](https://github.com/miyako/4d-plugin-image-dpi)

```4d
status:=Set image DPI(image;dpi)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">image</div>
  <div class="syntax-td cell cell--2">PICTURE</div>
  <div class="syntax-td cell cell--8"></div>        
  <div class="syntax-td cell cell--2">dpi</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>   
</div>

書き換える箇所は画像フォーマットによって違います。

* ``.bmp``

``BITMAPINFOHEADER``構造体の``biXPelsPerMeter``および``biYPelsPerMeter``フィールドを書き換えます。メートル毎ピクセル数に変換するため，DPI値は近似値となります。

* ``.png``

``pHYs``チャンクの単位（``PNG_RESOLUTION_METER``）と値を書き換えます。メートル毎ピクセル数に変換するため，DPI値は近似値となります。``tEXt`` ``zTXt`` ``iTXt``チャンクにも解像度に関する情報が含まれる可能性があるため，これらのタグは省略されます（解像度だけを変換できれば良いのですが・・・）。

* ``.jpg``

``JPEG_APP0``マーカーのDPI値を書き換えます。``IPTC_JPEG_MARKER``マーカーにも解像度に関する情報が含まれる可能性があるため，このマーカーは省略されます（解像度だけを変換できれば良いのですが・・・）。


* ``.tif``

``TIFFTAG_RESOLUTIONUNIT``フィールドを``RESUNIT_INCH``に設定し，``TIFFTAG_XRESOLUTION``および``TIFFTAG_YRESOLUTION``のDPI値を書き換えます。
