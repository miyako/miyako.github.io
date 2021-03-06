---
layout: simple
title: Input Scope
tags: plugin text japanese windows userinterface v17
---

Simple wrapper for [SetInputScope](https://docs.microsoft.com/ja-jp/windows/win32/api/inputscope/nf-inputscope-setinputscope).

<!--more-->

[miyako/4d-plugin-input-scope](https://github.com/miyako/4d-plugin-input-scope)

```
status:=Set input scope (scope)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">scope</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">InputScope Enumeration</div>  
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>      
</div>

#### Options

[InputScope Enumeration](https://docs.microsoft.com/en-us/windows/win32/api/inputscope/ne-inputscope-inputscope)の定数をそのまま渡すことができます。

```
success:=Disable input method ()
```

進行中の入力コンテキストをキャンセルし，フォーカスオブジェクトから入力メソッドの関連付けを外します。``On Getting Focus``イベントで使用されることが想定されています。

**注記**: `On Getting Focus`でカレントのテキスト入力のIMEを`disable`することはできないようです（イベント後に4DがIMEコンテキストを関連づけている疑い）。下記のように回避することができます。

```4d
Case of 
    : (FORM Event.code=On Getting Focus)

        CALL FORM(current form window;"Disable input methodを呼ぶだけのプロジェクトメソッド")

End case 
```
