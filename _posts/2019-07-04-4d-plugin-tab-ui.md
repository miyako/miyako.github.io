---
layout: simple
title: Window Tabbing
tags: plugin userinterface mac v17
---

Window tabbing for macOS.

<!--more-->

[miyako/4d-plugin-tab-ui](https://github.com/miyako/4d-plugin-tab-ui)

---

* サンプルプログラムは，プロジェクトモードで開いてください。（17r5以降）

* macOS 10.12以降（``TOGGLE WINDOW TAB OVERVIEW``のみ 10.13以降）

```
id:=Get window tab id (window)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">id</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">window</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

Returns the window tabbing identifier. Windows with matching IDs can merge.

```
SET WINDOW TAB ID (window;id{;mode})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">window</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>    
  <div class="syntax-td cell cell--2">id</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">mode</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div> 
</div>

Pass ``1`` in mode to force tabbing. Pass ``0`` to respect system preferences. 

Passing an empty string will disable tabbing (merged windows stay merged).

**Note**: You can merge your custom window with design mode windows by assigning the ID ``4D Forms and Methods``.

![](https://user-images.githubusercontent.com/1725068/60555052-a961bc80-9d75-11e9-8b76-8b484a798d0e.png){:.image .image--xl .shadow}


```
TOGGLE WINDOW TAB OVERVIEW (window)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">window</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

Invokes [``toggleTabOverview:``](https://developer.apple.com/documentation/appkit/nswindow/2870175-toggletaboverview?language=objc)

`macOS 10.13+`{:.info}

![](https://user-images.githubusercontent.com/1725068/60555051-a8c92600-9d75-11e9-869e-712b3c3db19f.png){:.image .image--xl .shadow}

```
TOGGLE WINDOW TAB BAR (window)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">window</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

**Note**: By default, a tabbable window with single member has no tab bar. If the window contains multiple members, the tab bar can not be hidden.

```
MERGE ALL WINDOWS (window)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">window</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

Merges all other windows with the same ID to the specified window.

```
SELECT NEXT WINDOW TAB (window)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">window</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

```
SELECT PREVIOUS WINDOW TAB (window)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">window</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>
