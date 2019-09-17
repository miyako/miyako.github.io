---
layout: simple
title: XSLT
tags: plugin xml v17
---

XSLT based on [libxml](http://xmlsoft.org/index.html).

<!--more-->

[miyako/4d-plugin-xslt](https://github.com/miyako/4d-plugin-xslt)

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
