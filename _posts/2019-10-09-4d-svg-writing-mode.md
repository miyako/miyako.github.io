---
layout: simple
title: SVG writing-mode
tags: svg japanese
---

4DのSVGレンダリングエンジンの縦書きサポートに関する考察です。

<!--more-->

---

#### Specification

4DのSVGレンダリングエンジンは，[Scalable Vector Graphics (SVG) 1.1 (Second Edition)](https://www.w3.org/TR/SVG11/)をベースに設計されており，基本的な要素や属性がサポートされています（つまり，すべてが利用できるわけではありません）。加えて，[Scalable Vector Graphics (SVG) Tiny 1.2 Specification](https://www.w3.org/TR/SVGTiny12/)の要素や属性も一部がサポートされています。

#### text or textArea

[``textArea``](https://www.w3.org/TR/SVGTiny12/text.html)は，四角形の内部にテキストをレンダリングするものです。折り返しや禁則処理を自前で実装する必要がなく，レイアウトが簡単にデザインできるので，とても便利です。ただし，2019年の時点で，主要なユーザーエージェントは``textArea``を[サポートしていない](https://caniuse.com/#search=svg)ので，外部アプリケーションで表示するような用途には不向きとなっています。

レイアウト関連では，下記のCSSスタイル属性がサポートされています。

* [``text-align``](https://www.w3.org/TR/SVGTiny12/text.html#TextAlignProperty) テキスト進行方向の揃え [start, end. center, justify]
* [display-align](https://www.w3.org/TR/SVGTiny12/text.html#DisplayAlignProperty) ブロック進行方向の揃え [auto, before, after, center]
* [letter-spacing](https://www.w3.org/TR/SVG11/text.html#LetterSpacingProperty)

縦書きスクリプトがサポートされているので，水平揃え・垂直揃えという表現はしない点に留意してください。

下記のCSSスタイル属性はサポートされていません。

* line-increment
* word-spacing
* glyph-orientation-horizontal
* glyph-orientation-vertical
* dominant-baseline

``textArea``は，指定した領域に収まるよう，テキストを描画するのに適しています。ただし，**行間をコントロールすることができない**ので，レイアウトのデザインに限界があります。

<img width="275" alt="スクリーンショット 2019-10-09 16 39 32" src="https://user-images.githubusercontent.com/1725068/66461160-63726e00-eab3-11e9-87d9-7a8650c647d6.png">

``text``は，どのユーザーエージェントでもサポートされている基本の要素です。テキストが複数行にわたる場合，``textArea``のように[``tbreak``](https://www.w3.org/TR/SVGTiny12/text.html#tbreakElement)要素で改行したり，レンダリングエンジンに折り返しの処理を任せたりするようなことはせず，行毎に``text``を使用します。手間はかかりますが，行間を自由に制御することができるというメリットがあります。

<img width="197" alt="スクリーンショット 2019-10-09 16 39 19" src="https://user-images.githubusercontent.com/1725068/66461150-5d7c8d00-eab3-11e9-83fc-0108b559945c.png">

この例では，本文に``text``，ルビに``textArea``を使用しています。座標とフォントサイズの単位に``pc``（パイカ）および``in``（インチ）を使用しているため，比較的シンプルにレイアウトを決めることができました。

``text``または``textArea``を縦書きにする場合，要素の``writing-mode``属性を指定します。CSSスタイルで指定することはできないので，注意してください。

#### Download

[https://github.com/miyako/4d-tips-svg-writing-mode](https://github.com/miyako/4d-tips-svg-writing-mode)

#### Convert to PDF (fail)

SVGをPDFに変換する[``rsvg-convert``](https://github.com/GNOME/librsvg)というプログラムがあります。

**カスタマイズ版**: [miyako/console-rsvg-convert](https://github.com/miyako/console-rsvg-convert)

上記の方法で作成したSVGを処理させたところ，下記のようなエラーが返されました。

```
Pango-WARNING **: couldn't load font "Times New Roman, Rotated-Left 12", modified variant/weight/stretch as fallback, expect ugly output.
```

```
Pango-ERROR **: Could not load fallback font, bailing out.
```

日本語の``writing-mode:tb-rl``でエラーになるようです。英語の縦書きでは問題ありませんでした。いずれにしても``textArea``は出力されません。

#### Convert to PDF (success)

4Dの印刷コマンドでPDFを作成することができます。

まず，印刷は同時に複数のプロセスで実行できないので，``Storage``でコードブロックを保護します。従来のように``Semaphore``を使用しても構いません。

```
If (Storage.mutex=Null)
	Use (Storage)
		Storage.mutex:=New shared object
	End use 
End if 

If (Storage.mutex.printing=Null)
	Use (Storage.mutex)
		Storage.mutex.printing:=New shared object
	End use 
End if 

Use (Storage.mutex.printing)

//...

End use 
```

カレントの印刷設定をオブジェクト型に保存します。

```
	C_OBJECT($currentPrintSettings)
	
	C_REAL($left;$top;$right;$bottom)
	GET PRINTABLE MARGIN($left;$top;$right;$bottom)
	
	C_LONGINT($destination)
	GET PRINT OPTION(Destination option;$destination)
	
	$currentPrintSettings:=New object(\
	"name";Get current printer;\
	"destination";$destination;\
	"margin";New object(\
	"left";$left;\
	"top";$top;\
	"right";$right;\
	"bottom";$bottom)\
	)
```

PDFファイルの保存パスを設定します。Macでは``Destination option``が``2``，Windowsでは``3``となる点に注意してください。

```
	If (Is Windows)
		SET CURRENT PRINTER(Generic PDF driver)
		SET PRINT OPTION(Destination option;2;$pdfPath)
	Else 
		
		SET PRINT OPTION(Destination option;3;$pdfPath)
	End if 
```

印刷コマンド終了後，印刷設定を復元します。

```
	SET CURRENT PRINTER($currentPrintSettings.name)
	SET PRINT OPTION(Destination option;$currentPrintSettings.destination)
	SET PRINTABLE MARGIN(\
	$currentPrintSettings.margin.left;\
	$currentPrintSettings.margin.top;\
	$currentPrintSettings.margin.right;\
	$currentPrintSettings.margin.bottom)
```

SVGは，用紙サイズぴったりのピクチャオブジェクトに転写して印刷します。フォームエディターで個別に用意することもできますが，JSONフォームであれば，オンザフライでフォームが作成できるので便利です。

```
C_OBJECT($form)

$form:=New object(\
"destination";"detailScreen";\
"rightMargin";0;\
"bottomMargin";0;\
"markerHeader";0;\
"markerBody";0;\
"markerBreak";0;\
"markerFooter";0;"events";New collection("onLoad";"onUnload");\
"pages";New collection(Null;New object("objects";New object)))

$form.pages[1].objects.img:=New object(\
"type";"input";\
"top";0;\
"left";0;\
"width";$width;\
"height";$height;\
"dataSourceTypeHint";"picture";\
"focusable";False;\
"enterable";False;\
"contextMenu";"none";\
"dragging";"none")
```

フォームの代わりにオブジェクト型をメモリにロードし，印刷ジョブを開始します。

```
OPEN PRINTING JOB

FORM LOAD($form)

$img:=OBJECT Get pointer(Object named;"img")
```

ピクチャをメモリ上の仮想フォームオブジェクトに代入します。

```
$img->:=$svg
$printed:=Print object(*;"img")
```

仮想フォームをアンロードし，印刷ジョブを終了します。

```
FORM UNLOAD

CLOSE PRINTING JOB
```
