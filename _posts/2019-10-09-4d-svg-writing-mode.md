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


<img width="197" alt="スクリーンショット 2019-10-09 16 39 19" src="https://user-images.githubusercontent.com/1725068/66461150-5d7c8d00-eab3-11e9-83fc-0108b559945c.png">
<img width="275" alt="スクリーンショット 2019-10-09 16 39 32" src="https://user-images.githubusercontent.com/1725068/66461160-63726e00-eab3-11e9-87d9-7a8650c647d6.png">
