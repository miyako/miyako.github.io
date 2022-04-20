---
layout: simple
title: Custom URL
tags: Windows macOS
---

Register a custom URL scheme

<!--more-->

#### Syntax

```
REGISTER PROTOCOL(scheme;method)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">scheme</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8"></div>  
<div class="syntax-td cell cell--2">method</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8">callback method name. signature is C_TEXT($1)</div>    
</div>

#### Usage

```

$scheme:="fourd"

REGISTER PROTOCOL($scheme;"MYCALLBACK")

//generate test page with custom hyperlinks

var $file : 4D.File
var $HTML : Text

$file:=Folder(fk resources folder).file("template.html")
$HTML:=$file.getText()
PROCESS 4D TAGS($HTML; $HTML; $scheme)
$file:=Folder(fk resources folder).file("example.html")
$file.setText($HTML)

OPEN URL($file.platformPath)
```

### macOS

A custom app is used to updated Launch Services. The app does not have any URL schemes in its `info.plist` but we need it to call `LSSetDefaultHandlerForURLScheme`. It is launched automatically in the background when necessary.

The app serves as a delegate. It sends the system-wide notification which is caught by the plugin. The notification identifier is `com.4D.Protocol`.

The notification is sent like:

```
CFDictionaryRef userInfo = CFDictionaryCreate(kCFAllocatorDefault,
                                              {CFSTR("url")},
                                              {(CFStringRef)urlString},
                                              1, NULL, NULL);
CFNotificationCenterPostNotification(CFNotificationCenterGetDistributedCenter(),
                                     (CFStringRef)notificationId,
                                     NULL,
                                     (CFDictionaryRef)userInfo,
                                     true);

```

### Windows

* [ブラウザ上のリンクから任意のデスクトップアプリのファイルを開けると超便利](https://qiita.com/kojimadev/items/74100c8557a92939ef69)

* [`UrlAssociations`](https://docs.microsoft.com/en-us/windows/win32/shell/default-programs#urlassociations) subkey

* [Launch the default app for a URI](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/launch-default-app)

* https://stackoverflow.com/questions/37702082/internet-explorer-or-edge-how-to-display-the-warning-that-appear-if-you-open-c
