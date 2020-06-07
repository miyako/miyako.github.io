---
layout: simple
title: phonetic
tags: plugin japanese userinterface v17
---

漢字のよみを取得

<!--more-->

[miyako/4d-plugin-kana](https://github.com/miyako/4d-plugin-kana/)

```4d
result:=Phonetic(string)
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
</div>

```4d
results:=Phonetics(string{;options})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">results</div>
  <div class="syntax-td cell cell--2">COLLECTION</div>
  <div class="syntax-td cell cell--8"></div>        
  <div class="syntax-td cell cell--2">string</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">options</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>    
</div>

オブジェクトのコレクションが返されます。

* ``word``: 文節
* ``yomi``: よみ

#### options

* ``width``: 全角 ``full`` 半角  ``half``
* ``format``: ひらがな ``hiragana`` カタカナ ``katakana``

デフォルトは「全角ひらがな」です。

* ``mode``: ***Windows only*** 形態素分解 ``detail``

Windows [品詞コード](https://docs.microsoft.com/en-us/previous-versions/office/developer/office-2007/ee815978%28v%3doffice.12%29)

Macの``NSLinguisticTagger``は日本語の``NSLinguisticTagSchemeLexicalClass``をサポートしていないようです。
