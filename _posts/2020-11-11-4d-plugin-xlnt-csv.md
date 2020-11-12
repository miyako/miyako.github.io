---
layout: simple
title: XLSX to CSV
tags: utility v18
---

XLSXを単純にCSV変換する

<!--more-->

[miyako/4d-plugin-xlsx-to-csv/](https://github.com/miyako/4d-plugin-xlsx-to-csv/)

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  
  <div class="syntax-td cell cell--2">path</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">XLSXファイルのパス</div>   
  
  <div class="syntax-td cell cell--2">sheets</div>
  <div class="syntax-td cell cell--2">ARRAY TEXT</div>
  <div class="syntax-td cell cell--8">シート名の配列（省略時: すべてのシート）</div>   
  
  <div class="syntax-td cell cell--2">password</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">XLSXファイルのパスワード（設定されている場合）</div>  
  
  <div class="syntax-td cell cell--2">folder</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">CSVファイル出力のフォルダーパス</div>  
  
  <div class="syntax-td cell cell--2">fldDelimit</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">フィールド区切り文字（省略時: カンマ）</div>  
  
  <div class="syntax-td cell cell--2">recDelimit</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">レコード区切り文字（省略時: CRLF）</div>  
</div>

  <div class="syntax-td cell cell--2">encoding</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">エンコーディング（省略時: BOM付きUTF-8）</div>  
</div>

```4d
convert xlsx to csv(path;sheets;password;folder;fldDelimit;recDelimit;encoding)
```

```4d
get xlsx sheets(&T;&Y;&T)(path;sheets;password)
```
#### エンコーディング

値|モード
--|----
0 | BOM付きUTF-8（デフォルト）
1 | BOM無しUTF-8
2 | Shift_JIS
