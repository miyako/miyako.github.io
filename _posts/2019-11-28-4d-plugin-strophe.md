---
layout: simple
title: strophe
tags: plugin network v17
---

XMPP support based on [libstrophe](http://strophe.im/libstrophe/).

<!--more-->

[miyako/4d-plugin-strophe](https://github.com/miyako/4d-plugin-strophe/)

#### Getting started

Download and install an XMPP server, e.g. [ejabberd Community Server](https://www.ejabberd.im).

For example, on Mac:

```
brew install ejabberd
```

[Setup TLS](https://blog.process-one.net/securing-ejabberd-with-tls-encryption/)

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







---

Start it

```
ejabberdctl start
```

Create a user 

```
ejabberdctl register jimmy.kimmel localhost abc
```

Create another user 

```
ejabberdctl register jimmy.fallon localhost nbc
```

Create another user for admin

```
ejabberdctl register admin localhost cbs
```

Login ad admin at [http://localhost:5280/admin/](http://localhost:5280/admin/)

Edit ejabberd.yml

```yml
acl:
  local:
    user_regexp: ""
  loopback:
    ip:
      - 127.0.0.0/8
      - ::1/128
  admin:
      - user: admin@localhost
```

Restart server

```
ejabberdctl restart
```

Refresh browser
