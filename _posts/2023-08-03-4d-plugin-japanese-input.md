---
layout: simple
title: Input
tags: plugin userinteraface
---

Macの日本語入力プログラムを簡単に制御するプラグイン

<!--more-->

[miyako/44d-tips-japanese-input](https://github.com/miyako/4d-tips-japanese-input)

#### Syntax

```
INPUT SET JAPANESE ({mode})
INPUT SET ASCII ({mode})
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">mode</div>
<div class="syntax-td cell cell--2">LONGINT</div>
<div class="syntax-td cell cell--8">使用するAPI</div>   
</div>

#### Kana Conversion Mode

定数|型|値
------------|------|----
`INPUT_API_CARBON` | LONGINT| 1
`INPUT_API_KEYCODE` | LONGINT|  2

* `INPUT_API_CARBON`: `TISSelectInputSource`をメインスレッドで実行します。日本語の入力ソースは`TISCopyInputSourceForLanguage(CFSTR("ja-JP")`で特定します。複数の入力メソッドが該当する場合，直近に選択されていたものが使用されます。英数の入力ソースは`TISCopyCurrentASCIICapableKeyboardInputSource`で特定します。

* `INPUT_API_KEYCODE`: `CGEventPost`を`kCGEventSourceStateHIDSystemState`で実行します。つまり，キー入力をシミュレートします。日本語の入力ソースは`kVK_JIS_Kana`キー，英数の入力ソースは`kVK_JIS_Eisu`で選択します。したがってJISキーボードが前提です。