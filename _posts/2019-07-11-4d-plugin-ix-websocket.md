---
layout: simple
title: WebSocket
tags: plugin network v17
---

Simple websocket based on [IXWebSocket](https://github.com/machinezone/IXWebSocket).

<!--more-->

[miyako/4d-plugin-ix-websocket](https://github.com/miyako/4d-plugin-ix-websocket)

---

* サンプルプログラムは，プロジェクトモードで開いてください。（17r5以降）

* オブジェクト型を使用しています。（v17以降）

* スレッドセーフです。

```
server:=Websocket server ({options})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">server</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">options</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8">see below</div>   
</div>

Creates a websocket server object.

サーバーオブジェクトを作成して返します。

#### Options

Property|Type|Description
------------|------|----
method|TEXT|name of project method to invoke on event
window|LONGINT|value passed on as parameter to method (``$4``)
process|LONGINT|value passed on as parameter to method (``$5``)
port|LONGINT|used to configure the server 
host|TEXT|used to configure the server 
backlog|LONGINT|used to configure the server 
maxConnections|LONGINT|used to configure the server 

The return object contains the current configuration plus a ``ref`` property.

```
client:=Websocket client ({options})
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">client</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8"></div>  
<div class="syntax-td cell cell--2">options</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8">see below</div>   
</div>

Creates a websocket client object.

クライアントオブジェクトを作成して返します。

#### Options

Property|Type|Description
------------|------|----
method|TEXT|name of project method to invoke on event
window|LONGINT|value passed on as parameter to method (``$4``)
process|LONGINT|value passed on as parameter to method (``$5``)
url|TEXT|used to configure the client 
pingInterval|LONGINT|used to configure the client 
pingTimeout|LONGINT|used to configure the client 
enableAutomaticReconnection|BOOLEAN|used to configure the client 
enablePong|BOOLEAN|used to configure the client 
perMessageDeflate|OBJECT|used to configure the client 
perMessageDeflate.enabled|BOOLEAN|used to configure the client 
perMessageDeflate.clientNoContextTakeover|BOOLEAN|used to configure the client 
perMessageDeflate.serverNoContextTakeover|BOOLEAN|used to configure the client 
perMessageDeflate.serverMaxWindowBits|LONGINT|used to configure the client 
perMessageDeflate.clientMaxWindowBits|LONGINT|used to configure the client 
disablePerMessageDeflate|BOOLEAN|mutually excludive with ``perMessageDeflate``

The return object contains the current configuration plus a ``ref`` property.
