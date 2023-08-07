---
layout: simple
title: Input
tags: plugin userinteraface
---

Macの日本語入力プログラムを簡単に制御するプラグイン

<!--more-->

[miyako/4d-plugin-text-input-service-v2](https://github.com/miyako/4d-plugin-text-input-service-v2)

#### Syntax

```
INPUT SET SOURCE (identifier)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">identifier</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8"></div>   
</div>

* pass a string returned from `INPUT Get source` in `identifier`.

* pass a [RFC 4647](https://www.ietf.org/rfc/rfc4647.txt) or [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) as `identifier` to specify a language.

* pass the string "ASCII" or an empty string to specify the current ascii capable keyboard input source.

```
source:=INPUT Get source ({identifier})
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">identifier</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8"></div>   
<div class="syntax-td cell cell--2">source</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8"></div>   
</div>

* pass a [RFC 4647](https://www.ietf.org/rfc/rfc4647.txt) or [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) as `identifier` to specify a language.

* pass an empty string to request the current input source.

* pass the string "ASCII" to request the current ascii capable keyboard input source.

```
INPUT SOURCE LIST (sources)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">sources</div>
<div class="syntax-td cell cell--2">COLLECTION</div>
<div class="syntax-td cell cell--8"></div>   
</div>
