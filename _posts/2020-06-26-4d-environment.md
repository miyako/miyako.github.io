---
layout: simple
title: Environment
tags: plugin v17
---

環境変数の読み書き

<!--more-->

[miyako/4d-plugin-environment](https://github.com/miyako/4d-plugin-environment/)

```4d
value:=Expand environment string(string)
```

* Windows限定

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">string</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>        
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>   
</div>

```4d
value:=Get environment variable(name)
PUT ENVIRONMENT VARIABLE (name;value)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">name</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>        
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>   
</div>

**注記**: WIndowsプログラムは，起動時に環境変数のコピーを受け取ります。システムまたはユーザーの環境変数はレジストリに書き込まれていますが，これを更新した場合，すでに起動中のプログラムの環境変数は変更されません。環境変数を書き換えたプログラムは，``WM_SETTINGCHANGE``メッセージを受信し，起動中のプログラムに環境の変化を通知することができます。このプログラムは，MDIウィンドウにメッセージハンドラーをインストールし，メッセージを受信すると，レジストリから環境変数を読み直します（削除された環境変数は，そのまま残されます）。

---

#### SDI mode support

Added new experimental command:

```
REGISTER ENVIRONMENT WINDOW(window)
```

Normally, the plugins installs a custom event handler for the MDI window. This command is Intended for SDI mode although it will work in either mode. Use it to attach a custom event handler in one of your SDI windows. Calling the command again will reset the previous call. 

**Note**: The window can not be a MDI child window. In MDI mode, use **Movable form dialog box**.

There is nothing special to do other than to register a capable window. The custom event handler is disposed automatically when the window is closed.
