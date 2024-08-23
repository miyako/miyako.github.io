---
layout: simple
title: Simple SQLite Client
tags: plugin connectivity
---

Simple SQLite client based on the tutorial from [sqlitetutorial.net](https://www.sqlitetutorial.net/sqlite-select/). 

<!--more-->

[miyako/4d-plugin-simple-sqlite-client](https://github.com/miyako/4d-plugin-simple-sqlite-client/)

```
status:=SQLite EXECUTE (path;sql{;values{;format}})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">path</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">path for sqlite3_open</div>
  <div class="syntax-td cell cell--2">sql</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">command for sqlite3_prepare_v2</div>   
  <div class="syntax-td cell cell--2">values</div>
  <div class="syntax-td cell cell--2">COLLECTION</div>
  <div class="syntax-td cell cell--8">values for sqlite3_bind_(text|double|int|null)</div>    
  <div class="syntax-td cell cell--2">format</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">see below</div>    
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>      
</div>

* Blob is returned as base64 text.
* Null is returned as null.
* Float is returned as double.
* Text is returned as text.
* Other types are ignored.

#### Integer Format 

Property|Type|Description
------------|------|----
SQLite Integer Simple | LONGINT| 0
SQLite Integer Complex | LONGINT| 1

In complex mode, the value is returned as an object with 2 properties: `intValue` `int64Value` (text)

In simple mode, the value is returned as integer.
