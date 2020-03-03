---
layout: simple
title: Simple SQLite Client
tags: plugin connectivity v17
---

Simple SQLite client using [libsqlite3](https://www.sqlite.org/index.html).

<!--more-->

[miyako/4d-plugin-simple-sqlite-client](https://github.com/miyako/4d-plugin-simple-sqlite-client/)

```
status:=status:=SQLite EXECUTE (path;SQL{;params{;mode}})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">path</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">SQL</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>    
  <div class="syntax-td cell cell--2">params</div>
  <div class="syntax-td cell cell--2">COLLECTION</div>
  <div class="syntax-td cell cell--8"></div>     
  <div class="syntax-td cell cell--2">mode</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>     
</div> 

#### SQLite Integer Format

Property|Type|Description
------------|------|----
SQLite Integer Simple | LONGINT| 0
SQLite Integer Complex | LONGINT|  1

If ``SQLite Integer Simple`` is passed, columns of type ``SQLITE_INTEGER`` are returned as ``int``.

If ``SQLite Integer Complex`` is passed, columns of type ``SQLITE_INTEGER`` are returned as objects, where each item has two properties: ``intValue`` which is ``int`` and ``int64Value`` which is text.
