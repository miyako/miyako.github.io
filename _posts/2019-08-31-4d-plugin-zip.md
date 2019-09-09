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

#### Compatibility note

There are several ways to create a zip file from an app on macOS. Not all of them are valid.

* Archive Utility

``/System/Library/CoreServices/Applications``

When a zip file is created via the Finder, the result is essentailly the same as using ``ditto`` with the option ``--sequesterRsrc``.

```sh
ditto -c -k --sequesterRsrc --keepParent test test.zip 
```

**Note**: The source and destination paths are passed in the reverse order for ``ditto`` compared to ``zip`` or ``minizip``.

```
drwxr-xr-x  2.1 unx        0 bx stor 19-Sep-09 14:18 test/
-rw-r--r--  2.1 unx     6148 bX defN 19-Sep-09 14:17 test/.DS_Store
drwxrwxr-x  2.1 unx        0 bx stor 19-Sep-09 14:18 __MACOSX/
drwxrwxr-x  2.1 unx        0 bx stor 19-Sep-09 14:18 __MACOSX/test/
-rw-r--r--  2.1 unx      120 bX defN 19-Sep-09 14:17 __MACOSX/test/._.DS_Store
drwxr-xr-x  2.1 unx        0 bx stor 19-Sep-09 14:16 test/folder/
lrwxr-xr-x  2.1 unx       33 b- stor 19-Sep-09 14:18 test/a
7 files, 6301 bytes uncompressed, 338 bytes compressed:  94.6%
```

We can assertain a few things:

1. Invisble files are stored
1. Symbolic links are stored
1. Resource forks and HFS meta-data are stored in a directory named ``__MACOSX``
1. UNIX file attributes are stored
1. Platform is ``unx``

<i class="fa fa-external-link" aria-hidden="true"></i> [ditto](https://www.unix.com/man-page/osx/1/ditto/)

* Minizip (zlib version)

[madler/zlib/contrib/minizip](https://github.com/madler/zlib/tree/master/contrib/minizip)

```sh
minizip test.zip test
```

```
-rw----     0.0 fat        0 b- defN 80-Jan-00 00:00 test
1 file, 0 bytes uncompressed, 2 bytes compressed:  0.0%
```

We can see that the program is quite limited.

1. Invisble files are NOT stored
1. Symbolic links are NOT stored
1. UNIX file attributes are NOT stored
1. Dates are NOT stored
1. Platform is ``fat``

* Zip

``/usr/bin/zip``

```sh
zip -r -y test.zip test
```

```sh
Zip file size: 893 bytes, number of entries: 4
drwxr-xr-x  3.0 unx        0 bx stor 19-Sep-09 14:18 test/
-rw-r--r--  3.0 unx     6148 bx defN 19-Sep-09 14:27 test/.DS_Store
drwxr-xr-x  3.0 unx        0 bx stor 19-Sep-09 14:16 test/folder/
lrwxr-xr-x  3.0 unx       33 bx stor 19-Sep-09 14:18 test/a
```

1. Invisble files are stored
1. Symbolic links are stored
1. UNIX file attributes are stored
1. Platform is ``unx``

<i class="fa fa-external-link" aria-hidden="true"></i> [zip](https://www.unix.com/man-page/osx/1/zip/)

* Minizip (nmoinvaz version)

[nmoinvaz/minizip/](https://github.com/nmoinvaz/minizip)

```sh
minizip -y test.zip test
```
`
```
Zip file size: 764 bytes, number of entries: 3
-rw-r--r--  6.3 osx     6148 bX defN 19-Sep-09 14:27 .DS_Store
drwxr-xr-x  6.3 osx        0 b- stor 19-Sep-09 14:16 folder/
lrwxr-xr-x  6.3 osx        0 bX defN 19-Sep-09 14:16 a
```

1. Invisble files are stored
1. Symbolic links are stored but the content (path) is missing
1. UNIX file attributes are stored
1. Platform is ``osx``

In order to keep integrity we want the following features:

1. Ignore invisble files 
1. Ignore Resource forks and HFS meta-data
1. Store symbolic links with their paths
1. Store UNIX file attributes 
1. Store dates 
1. Store platform as ``osx`` (optional)

Unfortunately, neither the ``madler`` or ``nmoinvaz`` seems to tick all boxes.

The plugin is based on the ``nmoinvaz`` ``minizip`` code with some modifications to ignore invisible files and store symbolic links with their paths. **This is critical to create a zip that can be unarchived on macOS 10.15 Catalina**.  

**Note**: If you transfer a zipped app over a network (AirDrop, email, FTP:,  HTTP:, etc.) the file will be marked with some Finder attributes that will signal GateKeeper to block its execution. You can remove such attributes with ``xattr -r -c`` or ``xattr -r -d com.apple.quarantine``. 

<i class="fa fa-external-link" aria-hidden="true"></i> [xattr](https://www.unix.com/man-page/osx/1/xattr/)

---

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
