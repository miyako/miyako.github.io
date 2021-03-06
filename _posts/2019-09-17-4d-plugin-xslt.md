---
layout: simple
title: XSLT
tags: plugin xml v17
---

XSLT based on [libxml](http://xmlsoft.org/index.html).

<!--more-->

[miyako/4d-plugin-xslt-v2](https://github.com/miyako/4d-plugin-xslt-v2)

#### Compatibility note

For simplicity, the command signature has been changed.

* Object instead of array pair
* BLOB I/O instead of text 
* Thread safe

#### Library information

* libxml2 ``2.9.9`` --with-threads
* libxslt ``1.1.33`` 

``xmlInitParser()`` is used in the "main" thread

[http://xmlsoft.org/threads.html](http://xmlsoft.org/threads.html)

```
result:=XSLT Apply stylesheet(xml;xsl;options)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">xml</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">xsl</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">options</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">result</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>    
</div>  

Pass key/value pair in ``options`` to set XSLT parameters. Keep in mind that XSLT parameters are always string. The numeric value ``123`` should be passed as ``"123"`` and string value ``abc`` should be passed as ``"'abc'"``. 

Reserved key names ``xmlParserOption`` and ``xslParserOption`` can be used to specify [xmlParserOption](http://xmlsoft.org/html/libxml-parser.html#xmlParserOption).

``xml`` and ``xsl`` can be a path or BLOB data. On Mac, the path should be HFS system path in UTF-8. On Windows, it is unclear whether the library expects ANSI or UTF-8. IF unsure, consider the BLOB option. 

For simlpicity, the plugin does not yield to 4D runtime during XSLT. If processing takes time, consider using a preemptive worker process.
