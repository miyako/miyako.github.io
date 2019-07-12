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
worker|TEXT|value passed on as parameter to method (``$5``)
window|LONGINT|value passed on as parameter to method (``$6``)
process|LONGINT|value passed on as parameter to method (``$7``)
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
worker|TEXT|value passed on as parameter to method (``$5``)
window|LONGINT|value passed on as parameter to method (``$6``)
process|LONGINT|value passed on as parameter to method (``$7``)
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
disablePerMessageDeflate|BOOLEAN|mutually exclusive with ``perMessageDeflate``

The return object contains the current configuration plus a ``ref`` property.

**Note**: The ``window``, ``worker`` and ``process`` paramters may be useful for ``CALL FORM``,  ``CALL WORKER`` or ``POST OUTSIDE CALL``.

#### Signature of callback method

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">server</div>
<div class="syntax-td cell cell--2">LONGINT</div>
<div class="syntax-td cell cell--8">0 for client side messages</div>  
<div class="syntax-td cell cell--2">client</div>
<div class="syntax-td cell cell--2">LONGINT</div>
<div class="syntax-td cell cell--8"></div>  
<div class="syntax-td cell cell--2">type</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8">open, close, error, fragment, ping, pong, message</div>   
<div class="syntax-td cell cell--2">context</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8">JSON format</div>   
<div class="syntax-td cell cell--2">worker</div>
<div class="syntax-td cell cell--2">TEXT</div>
<div class="syntax-td cell cell--8"> </div>   
<div class="syntax-td cell cell--2">window</div>
<div class="syntax-td cell cell--2">LONGINT</div>
<div class="syntax-td cell cell--8"></div>   
<div class="syntax-td cell cell--2">process</div>
<div class="syntax-td cell cell--2">LONGINT</div>
<div class="syntax-td cell cell--8"></div>   
</div>

The method is executed in a local process named ``$websocket_event_queue``. 

**Note**: Try not to abort this process from the debugger (let it exit gracefully). If a debug window displayed via ``TRACE`` is aborted, the callback method is no longer executed. By contrast, a debug window displayed via a break point does not prevent subsequent calls, but closing the application while such window is running may hang the application. You might want to delegate the response to a new process or a worker. In fact, that is the intended purpose of the parameters ``process``, ``window`` and ``worker``. 

#### Context

For message, ping, pong, fragment

Property|Type|Description
------------|------|----
wireSize|LONGINT|
binary|BOOLEAN|always ``false`` if the plugin is used to ``send()``
data|TEXT|

For open

Property|Type|Description
------------|------|----
uri|TEXT|

Headers are added as key value pair.

For error

Property|Type|Description
------------|------|----
decompressionError|BOOLEAN|
reason|TEXT|
http_status|LONGINT|
wait_time|REAL|
retries|LONGINT|

For close

Property|Type|Description
------------|------|----
code|LONGINT|
reason|TEXT|
remote|BOOLEAN|

```
status:=Websocket server start (server)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">status</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8"></div>  
<div class="syntax-td cell cell--2">server</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8">must at least contain ref</div>   
</div>

Start a websocket server.

サーバーを開始します。

The ``server`` object may optionally contain  ``method`` ``worker`` ``window`` ``process``  to modify current configuration. Other proprties are mutable.

#### Status

Property|Type|Description
------------|------|----
success|BOOLEAN|
message|TEXT|

```
status:=Websocket client start (client)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">status</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8"></div>  
<div class="syntax-td cell cell--2">client</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8">must at least contain ref</div>   
</div>

Start a websocket client.

クライアントを開始します。

The ``client`` object may optionally contain a connection ``timeout`` property (default: ``20`` seconds).

It may also contain ``method`` ``worker`` ``window`` ``process`` ``url`` ``pingInterval`` ``pingTimeout`` ``enableAutomaticReconnection`` ``enablePong`` ``perMessageDeflate`` ``disablePerMessageDeflate`` to modify current configuration.

#### Status

Property|Type|Description
------------|------|----
success|BOOLEAN|
http_status|LONGINT|
errorStr|TEXT|
uri|TEXT|
headers|OBJECT|

```
status:=Websocket server stop (server)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">status</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8"></div>  
<div class="syntax-td cell cell--2">server</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8">must at least contain ref</div>   
</div>

Stop a websocket server.

サーバーを停止します。

The ``server`` object may contain properties (see ``Websocket server start``) to be used the next time the server is started. The ``status`` object is a copy of the server object with updated properties.

```
status:=Websocket client stop (client)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">status</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8"></div>  
<div class="syntax-td cell cell--2">client</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8">must at least contain ref</div>   
</div>

Stop a websocket client.

クライアントを停止します。

The ``client`` object may contain properties (see ``Websocket client start``) to be used the next time the server is started. The ``status`` object is a copy of the client object with updated properties.

```
status:=Websocket server send (server;data)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">statuses</div>
<div class="syntax-td cell cell--2">COLLECTION</div>
<div class="syntax-td cell cell--8"></div>  
<div class="syntax-td cell cell--2">server</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8">must at least contain ref</div>   
<div class="syntax-td cell cell--2">data</div>
<div class="syntax-td cell cell--2">BLOB</div>
<div class="syntax-td cell cell--8"></div>   
</div>

Send data to connected clients.

クライアントにデータを送信します。

The ``server`` object may optionally contain a ``clients`` property, which is a collection of integer (client ``ref``) to send data to a select target. Otherwise, data is sent to all clients connected to the server. 

A status object is returned for each target.

#### Status

Property|Type|Description
------------|------|----
success|BOOLEAN|
compressionError|BOOLEAN|
payloadSize|LONGINT|
wireSize|LONGINT|
client|LONGINT|

```
status:=Websocket client send (client;data)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">status</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8"></div>  
<div class="syntax-td cell cell--2">client</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8">must at least contain ref</div>   
<div class="syntax-td cell cell--2">data</div>
<div class="syntax-td cell cell--2">BLOB</div>
<div class="syntax-td cell cell--8"></div>   
</div>

Send data to connected server.

サーバーにデータを送信します。

#### Status

Property|Type|Description
------------|------|----
success|BOOLEAN|
compressionError|BOOLEAN|
payloadSize|LONGINT|
wireSize|LONGINT|

```
status:=Websocket server clear (server)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">status</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8"></div>  
<div class="syntax-td cell cell--2">server</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8">must at least contain ref</div>    
</div>

Dispose a server.

サーバーオブジェクトを破棄します。

All remaining objects are automatically cleared on exit. 

The returned object is empty (unused).

```
status:=Websocket client clear (server)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">status</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8"></div>  
<div class="syntax-td cell cell--2">client</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8">must at least contain ref</div>    
</div>

Dispose a client.

クライアントオブジェクトを破棄します。

All remaining objects are automatically cleared on exit. 

The returned object is empty (unused).

```
status:=Websocket server clients (server)
```

<div class="grid">
<div class="syntax-th cell cell--2">Parameter</div>
<div class="syntax-th cell cell--2">Type</div>
<div class="syntax-th cell cell--8">Description</div>
<div class="syntax-td cell cell--2">clients</div>
<div class="syntax-td cell cell--2">COLLECTION</div>
<div class="syntax-td cell cell--8"></div>  
<div class="syntax-td cell cell--2">server</div>
<div class="syntax-td cell cell--2">OBJECT</div>
<div class="syntax-td cell cell--8">must at least contain ref</div>    
</div>

Returns a list of connected clients (integer ``ref``).

サーバーに接続しているクライアントの参照番号を返します。

