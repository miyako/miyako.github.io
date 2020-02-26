---
layout: simple
title: Simple PostgreSQL Client
tags: plugin connectivity v17
---

Simple PostgreSQL client based on [libpq](https://www.postgresql.org). 

<!--more-->

[miyako/4d-plugin-simple-postgres-client-v2](https://github.com/miyako/4d-plugin-simple-postgres-client-v2/)

```
status:=PQ EXECUTE (connect;sql{;params{;format}})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">connect</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">conninfo for PQconnectdb()</div>
  <div class="syntax-td cell cell--2">sql</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8">command for PQexecParams</div>   
  <div class="syntax-td cell cell--2">params</div>
  <div class="syntax-td cell cell--2">COLLECTION</div>
  <div class="syntax-td cell cell--8">parameters for PQexecParams</div>    
  <div class="syntax-td cell cell--2">format</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">see below</div>    
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>      
</div> 

#### Format 

Property|Type|Description
------------|------|----
PQ_RESULT_TEXT | LONGINT| 0
PQ_RESULT_BINARY | LONGINT| 1

``resultFormat`` passed to [``PQexecParams()``](https://www.postgresql.org/docs/9.1/libpq-exec.html).
