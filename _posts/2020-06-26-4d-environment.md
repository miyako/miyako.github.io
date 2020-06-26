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

**注記**: WIndowsでは，外部プロセスが書き換えた環境変数は，プロセスを再開するまで，反映されません。``WM_SETTINGCHANGE``メッセージを受信し，レジストリから読み取る方法もあるようですが，このプラグインでは実装されていません。
