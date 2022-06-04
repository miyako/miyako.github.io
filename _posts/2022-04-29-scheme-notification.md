---
layout: simple
title: Scheme Notification
tags: mac plugin userinterface
---

Switch from dark to light.

<!--more-->

[miyako/4d-plugin-appearance](https://github.com/miyako/4d-plugin-appearance)

#### Syntax

```
scheme:=Get system color scheme
scheme:=Get effective color scheme
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">scheme</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8">light, dark or auto</div>   
</div>

1. On Catalina and above, read `NSUserDefaults` `AppleInterfaceStyleSwitchesAutomatically` for "auto".

2. If not "auto", on Mojave or later, read `NSUserDefaults` `AppleInterfaceStyle` for "light" or "dark".

```
ON APPEARANCE CHANGE CALL(method)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">method</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8">#DECLARE($mode:Text) $1 is light or dark</div>   
</div>
