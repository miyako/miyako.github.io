---
layout: simple
title: strophe
tags: plugin network v17
---

XMPP support based on [libstrophe](http://strophe.im/libstrophe/).

<!--more-->

[miyako/4d-plugin-strophe](https://github.com/miyako/4d-plugin-strophe/)

#### About

This plugin is a minimal  ``proof of concept`` client for sending and receiving messages via [XMPP](https://en.wikipedia.org/wiki/XMPP). It covers only a fraction of what is actually possible with ``libstrophe``.  

XMPP enables the near-real-time exchange of structured yet extensible data between any two or more network entities. 

**near-real-time exchange**: ``libstrophe`` can be used to install [event handlers](http://strophe.im/libstrophe/doc/0.9.2/group___handlers.html) (``xmpp_handler_add``, ``xmpp_id_handler_add``, ``xmpp_timed_handler_add``), which are callback functions fired when a specific stanza arrives or periodically. For simplicity, the plugin does not maintain an open connection for receiving and responding to events. The "send message" command will simply send and disconnect. The "connect" command will simply check in, collect all offline (unread) messages, then disconnect. Put another way, you need to keep polling the server in 4D code to receive new messages. 

**structured yet extensible data**:  ``libstrophe`` can be used to create message, iq, error or presence [stanzas](http://strophe.im/libstrophe/doc/0.9.2/group___stanza.html) (a **stanza** is a unit of structured data, an abstraction of XML tree nodes), but it can be also be used to create generic stanza to handle any kind of structured information. For simplicity, the plugin only supports sending and receiving message stanzas. Of course, you can put any kind of data in the message body. You can also add any number of custom attributes.  

**between any two or more network entities**: This is the focus of this plugin. You can depend on existing network of XMPP servers to broker your message from one 4D to another. You can also depend on those servers to queue your messages.

#### Get started

You need 1 or more XMPP servers to relay your messages. 

For example, you could use [ejabberd Community Server](https://www.ejabberd.im) on Mac.

* Install [``homebrew``](https://brew.sh)

* Install ``ejabberd``

```
brew install ejabberd
```

* [Setup TLS](https://blog.process-one.net/securing-ejabberd-with-tls-encryption/)

```
openssl dhparam -out dh2048.pem 2048
```

```
openssl genrsa -out localhost-ejabberd.key 2048
```

```
openssl req -out localhost-ejabberd.csr -key localhost-ejabberd.key -new -sha256
```

```
openssl x509 -req -days 365 -in localhost-ejabberd.csr -signkey localhost-ejabberd.key -out localhost-ejabberd.crt
```

```
cat localhost-ejabberd.crt >  localhost-ejabberd.pem
cat localhost-ejabberd.key >> localhost-ejabberd.pem
```

Edit ``/usr/local/etc/ejabberd/ejabberd.yml``

```yml
#certfiles:
#  - "/etc/letsencrypt/live/localhost/fullchain.pem"
#  - "/etc/letsencrypt/live/localhost/privkey.pem"

listen:
  -
    port: 5222
    ip: "::"
    module: ejabberd_c2s
    max_stanza_size: 262144
    shaper: c2s_shaper
    access: c2s
    certfile: "/usr/local/etc/ejabberd/localhost-ejabberd.pem"
    starttls: true
    starttls_required: true
    tls_compression: false
    dhfile: "/usr/local/etc/ejabberd/dh2048.pem"
```

* Start ``ejabberd``

```
ejabberdctl start
```

* Create a user 

```
ejabberdctl register jimmy.kimmel localhost abc
```

* Create another user 

```
ejabberdctl register jimmy.fallon localhost nbc
```

* Create another user for admin

```
ejabberdctl register administrator localhost cbs
```

* Login as admin at [http://localhost:5280/admin/](http://localhost:5280/admin/)

* Edit ejabberd.yml

```yml
acl:
local:
  user_regexp: ""
loopback:
  ip:
    - "127.0.0.0/8"
    - "::1/128"
admin:
  user:
    - "administrator": "localhost"
```

* Restart server

```
ejabberdctl restart
```

* Refresh browser

<img width="556" alt="スクリーンショット 2019-11-29 10 09 38" src="https://user-images.githubusercontent.com/1725068/69837076-6bb78000-1290-11ea-9bfa-b0a6b8354091.png">

* Test that the server is woring, with an XMPP client

For example, you could use [Adium](https://adium.im) on Mac.

---

#### Send a message

```
$params:=New object

$params.jid:="jimmy.fallon@localhost/m"
$params.password:="nbc"
$params.host:="localhost"

  //message stanza
$message:=New object(\
"body";"Hello!";\
"type";"chat";\
"id";Generate UUID;\
"to";"jimmy.kimmel@localhost")

$status:=xmpp send message ($params;$message)
```

```
status:=xmpp send message (params;message)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">params</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">message</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

#### params object

Property|Type|Description
------------|------|----
jid|TEXT|required
password|TEXT|required
host|TEXT|required
logLevel|LONGINT|default=``XMPP_LEVEL_DEBUG``
keepAlive|BOOLEAN|default=``false``
keepAliveTimeout|LONGINT|default=``60``
keepAliveInterval|LONGINT|default=``1``
timeout|LONGINT|default=``20``
disableTLS|BOOLEAN|default=``false``
mandatoryTLS|BOOLEAN|default=``true``
legacyTLS|BOOLEAN|default=``false``
trustTLS|BOOLEAN|default=``true``
enableLegacyAuth|BOOLEAN|default=``false``

#### message object

Property|Type|Description
------------|------|----
body|TEXT|required
to|TEXT|required
type|TEXT|default="chat"
ns|TEXT|default="jabber:client"
from|TEXT|default=``jid``
xml:lang|TEXT|default="en"
id|TEXT|default=``xmpp_uuid_gen()``

#### status object

Property|Type|Description
------------|------|----
log|COLLECTION|

* Example

Message sent to an offline peer is banked.

<img width="556" alt="スクリーンショット 2019-11-29 10 33 22" src="https://user-images.githubusercontent.com/1725068/69837763-ba1a4e00-1293-11ea-9162-1a657245aec1.png">

<img width="556" alt="スクリーンショット 2019-11-29 11 07 28" src="https://user-images.githubusercontent.com/1725068/69838799-75dd7c80-1298-11ea-9925-f02e22211e82.png">

---

#### Receive messages

```
$params:=New object

$params.jid:="jimmy.kimmel@localhost/m"
$params.password:="abc"
$params.host:="localhost"

$status:=xmpp connect ($params)
```

```
status:=xmpp connect (params;message)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">params</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

#### status object

Property|Type|Description
------------|------|----
log|COLLECTION|
messages|COLLECTION|

#### message object

Property|Type|Description
------------|------|----
body|TEXT|
to|TEXT|
type|TEXT|
ns|TEXT|
from|TEXT|
id|TEXT|
