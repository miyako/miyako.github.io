---
layout: simple
title: kana
tags: plugin japanese userinterface v17
---

ひらがな⇄カタカナ・半角⇄全角の変換

<!--more-->

[miyako/4d-plugin-kana](https://github.com/miyako/4d-plugin-kana/)

```
result:=Convert kana(string{;mode})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">result</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>        
  <div class="syntax-td cell cell--2">string</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>      
  <div class="syntax-td cell cell--2">mode</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>          
</div>

#### Kana Conversion Mode

Property|Type|Description
------------|------|----
LCMAP_FULLWIDTH | LONGINT| 0
LCMAP_HALFWIDTH | LONGINT|  1
LCMAP_HIRAGANA | LONGINT| 0
LCMAP_KATAKANA | LONGINT|  2

なんとなく，Windows SDKの定数名をそのまま使用しています。当然，ひらがなとカタカナ，半角と全角は相互に排他的です。そして半角のひらがなは存在しません。デフォルトは``LCMAP_FULLWIDTH | LCMAP_HIRAGANA``，つまり「（カタカナから）全角ひらがなへの変換」になります。
