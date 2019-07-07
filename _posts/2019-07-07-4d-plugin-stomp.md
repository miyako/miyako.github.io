---
layout: simple
title: STOMP
tags: plugin network v17
---

Rewrite of STOMP client based on [libstomp](https://github.com/a3linux/libstomp).

<!--more-->

[miyako/4d-plugin-stomp](https://github.com/miyako/4d-plugin-stomp)

---

* サンプルプログラムは，プロジェクトモードで開いてください。（17r5以降）

* オブジェクト型を使用しています。（v17以降）

* スレッドセーフです。

* 動作確認には[ActiveMQ](http://activemq.apache.org/getting-started.html)を使用しました。

```
stomp:=STOMP Connect (host;port)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">host</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">port</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">stomp</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">context ID</div>    
</div>

```
error:=STOMP Disconnect (stomp)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">stomp</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">context ID</div>  
  <div class="syntax-td cell cell--2">error</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">see below</div>  
</div>

Error codes are negative [APR_ERRORNO](https://apr.apache.org/docs/apr/1.5/apr__errno_8h.html) or ``-1`` if the context ID was invalid. A ``winsock`` error code (which may be different across platforms) is returned in case of low level network failure.

```
error:=_o_STOMP Write (stomp;command;body;headerNames;headerValues{;timeout})
error:=_o_STOMP Read (stomp;command;body;headerNames;headerValues{;timeout})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">stomp</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">context ID</div>  
  <div class="syntax-td cell cell--2">command</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">body</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div> 
    <div class="syntax-td cell cell--2">headerNames</div>
  <div class="syntax-td cell cell--2">ARRAY TEXT</div>
  <div class="syntax-td cell cell--8"></div> 
      <div class="syntax-td cell cell--2">headerValues</div>
  <div class="syntax-td cell cell--2">ARRAY TEXT</div>
  <div class="syntax-td cell cell--8"></div> 
        <div class="syntax-td cell cell--2">timeout</div>
  <div class="syntax-td cell cell--2">LONGINT </div>
  <div class="syntax-td cell cell--8">I/O timeout in milliseconds; default is 3000</div> 
    <div class="syntax-td cell cell--2">error</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">see below</div>  
</div>

```
error:=STOMP Write (stomp;command;body;headers{;timeout})
error:=STOMP Read (stomp;command;body;headers{;timeout})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">stomp</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">context ID</div>  
  <div class="syntax-td cell cell--2">command</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">body</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div> 
    <div class="syntax-td cell cell--2">headers</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8">key value pair of header names and values</div> 
        <div class="syntax-td cell cell--2">timeout</div>
  <div class="syntax-td cell cell--2">LONGINT </div>
  <div class="syntax-td cell cell--8">I/O timeout in milliseconds; default is 3000</div> 
    <div class="syntax-td cell cell--2">error</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8">see below</div>  
</div>

Error codes are negative [APR_ERRORNO](https://apr.apache.org/docs/apr/1.5/apr__errno_8h.html) or ``-1`` if the context ID was invalid. A ``winsock`` error code (which may be different across platforms) is returned in case of low level network failure.
