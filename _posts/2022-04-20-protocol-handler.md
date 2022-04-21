---
layout: simple
title: Custom URL
tags: windows mac plugin
---

Register a custom URL scheme.

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

#### Getting started on macOS

Launch the *url-redirect* app once. It is important to do this manually for Finder to recognise the app as as a custom URL handler.

Run the command to register your custom URL scheme.

#### Getting started on Windows

Launch 4D as Administrator. This is necessary as the command needs to edit some registry keys.

Once registered, you can use the command as a regular user.

---

On both platforms, the 4D app itself is **not** the URL handler. Instead, a small helper app with no UI redirects the event using a platform specific messaging system. Your app will receive this notification if it uses the plugin and already runnining.
