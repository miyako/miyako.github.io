---
layout: simple
title: Zip
tags: plugin v17
---

Simple archiver based on [libminizip](https://github.com/nmoinvaz/minizip).

<!--more-->

[miyako/4d-plugin-zip](https://github.com/miyako/4d-plugin-zip)

---

* Updated to minizip ``2.8.9``

The previous version had a bug in detecting a directory path. As a result, the zip file had incorrect meta data; a folder was ``defN`` instead of ``stor``, which could be confirmed by ``zipinfo``. Mojave would unzip such files, but the unarchiver on Catalina would report the file as corrupt.

```
success:=Zip (src;dst;pass;level;options;callback;codepage)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">src</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">dst</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">pass</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">level</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">options</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>    
  <div class="syntax-td cell cell--2">callback</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">codepage</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">success</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

#### Zip options

Property|Type|Description
------------|------|----
ZIP_Ignore_hidden|LONGINT|
ZIP_With_attributes|LONGINT|
ZIP_Without_enclosing_folder|LONGINT|
ZIP_With_encryption|LONGINT|
ZIP_BZ2|LONGINT|
ZIP_7Z|LONGINT|

#### Zip Compression Level

Property|Type|Description
------------|------|----
ZIP_Compression_level_default|LONGINT|
ZIP_Compression_level_0|LONGINT|
ZIP_Compression_level_1|LONGINT|
ZIP_Compression_level_2|LONGINT|
ZIP_Compression_level_3|LONGINT|
ZIP_Compression_level_4|LONGINT|
ZIP_Compression_level_5|LONGINT|
ZIP_Compression_level_6|LONGINT|
ZIP_Compression_level_7|LONGINT|
ZIP_Compression_level_8|LONGINT|
ZIP_Compression_level_9|LONGINT|

#### Zip Charset

Property|Type|Description
------------|------|----
Zip_Charset_automatic|LONGINT|
{any}|LONGINT|windows code page

```
result:=Unzip (src;dst;pass;options;callback;codepage)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">src</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">dst</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">pass</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">options</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>    
  <div class="syntax-td cell cell--2">callback</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">codepage</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">success</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>
