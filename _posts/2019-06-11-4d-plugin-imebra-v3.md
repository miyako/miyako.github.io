---
layout: simple
title: Imebra
tags: plugin graphic v17
---

Simple DICOM reader using [Imebra](https://imebra.com) with some [LibGD](https://libgd.github.io) filters.

[miyako/4d-plugin-imebra-v3](https://github.com/miyako/4d-plugin-imebra-v3)

<!--more-->

---

### Syntax

```
images:=Imebra Get images (data{;options})
```

Parameter|Type|Description
------------|------|----
data|BLOB|DICOM file data
options|OBJECT|see below
images|OBJECT|see below

#### Options

Property|Type|Description
------------|------|----
format|TEXT|``.png`` ``.jpg`` ``.jpeg`` ``.gif`` ``.wbmp`` ``.webp`` ``.tif`` ``.tiff`` default:``.bmp``
quality|LONGINT|``.jpg``: ``0`` (default) to ``95``<br />n<br />``.webp``: ``-1`` (default) ``0`` to ``100``
level|LONGINT|``.png``: ``-1`` (default) ``0`` (none) ``1`` to ``9``
compression|LONGINT|``.bmp``: ``0`` (default) or ``1`` RLE compression
fg|LONGINT|``.wbmp``: foreground index
tags|BOOLEAN|``true`` to read DICOM tags
count|LONGINT|max number of images to read, ``-1`` read all images

#### Images

Property|Type|Description
------------|------|----
images|COLLECTION|
images\[\].colorspace|TEXT|
images\[\].format|TEXT|
images\[\].height|REAL|pixels
images\[\].width|REAL|pixels
images\[\].size|REAL|bytes
images\[\].image|PICTURE|

``fg``, ``quality``, ``level``, ``compression`` are optional

```
images:=Imebra Apply filters (data{;options})
```

Parameter|Type|Description
------------|------|----
data|BLOB|image data
options|OBJECT|see below
images|OBJECT|see below

#### Options

Property|Type|Description
------------|------|----
format|TEXT|``.png`` ``.jpg`` ``.jpeg`` ``.gif`` ``.wbmp`` ``.webp`` ``.tif`` ``.tiff`` default:``.bmp``
quality|LONGINT|``.jpg``: ``0`` (default) to ``95``<br />n<br />``.webp``: ``-1`` (default) ``0`` to ``100``
level|LONGINT|``.png``: ``-1`` (default) ``0`` (none) ``1`` to ``9``
compression|LONGINT|``.bmp``: ``0`` (default) or ``1`` RLE compression
fg|LONGINT|``.wbmp``: foreground index
filters|COLLECTION|see below

#### Filter

every element should be an object

Property|Type|Description
------------|------|----
filter|TEXT|``edgeDetectQuick``<br/>``emboss``<br/>``meanRemoval``<br/>``grayScale``<br/>``negate``<br/>``smooth``<br/>``brightness``<br/>``contrast``<br/>``scatter``<br/>``pixelate``<br/>``gaussianBlur``<br/>``color``<br/>``scatterColor``<br/>``convolution``
smooth|REAL|for ``smooth``
brightness|REAL|for ``brightness``
contrast|REAL|for ``contrast``
radius|LONGINT|for ``gaussianBlur``
sigma|REAL|for ``gaussianBlur``
sub|LONGINT|for ``scatter`` ``scatterColor``
plus|LONGINT|for ``scatter`` ``scatterColor``
size|LONGINT|for ``pixelate``
mode|LONGINT|for ``pixelate``
div|REAL|for ``convolution``
offset|REAL|for ``convolution``
matrix|COLLECTION|size: ``[3][3]`` of REAL for ``convolution``
colors|COLLECTION|of REAL for ``scatterColor``
red|LONGINT|for ``color``
green|LONGINT|for ``color``
blue|LONGINT|for ``color``
alpha|LONGINT|for ``color``
angle|LONGINT|for ``rotate``
dstW|LONGINT|for ``rotate``
dstH|LONGINT|for ``rotate``
dstX|LONGINT|for ``rotate``
dstY|LONGINT|for ``rotate``
srcW|LONGINT|for ``rotate``
srcH|LONGINT|for ``rotate``
srcX|LONGINT|for ``rotate``
srcY|LONGINT|for ``rotate``

filters are applied in the order they appear int the collection

the following filters take 0 params

- ``selectiveBlur``
- ``edgeDetectQuick``
- ``emboss``
- ``meanRemoval``
- ``grayScale``
- ``negate``

the following filters take 1 param

- ``smooth``: weight
- ``brightness``: brightness
- ``contrast``: contrast

the following filters take 2 params

- ``gaussianBlur``: radius, sigma
- ``scatter``: sub, plus
- ``pixelate``:  size, mode

the following filters take 3 params

- ``convolution``: matrix, div, offset
- ``scatterColor``: sub, plus, colors

the following filter takes 4 params

- ``color``: red, green, blue, alpha

the following filter takes 9 params

- ``rotate``: angle, dstW, dstH, dstX, dstY, srcW, srcH, srcX, srcY

#### Images

Property|Type|Description
------------|------|----
images|COLLECTION|
images\[0\].format|TEXT|
images\[0\].size|REAL|bytes
images\[0\].image|PICTURE|the image before the last filter
images\[1\].format|TEXT|
images\[1\].size|REAL|bytes
images\[1\].image|PICTURE|the image after the last filter

``fg``, ``quality``, ``level``, ``compression`` are optional

