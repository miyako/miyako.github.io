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

---

**Note**: Tested 28 Nov. 2019. The installer (``19.09.1``) or ``brew`` seems to have compatibility issues on Catalina. Constantly getting TLS error from libstrophe. [https://homebrew.bintray.com/bottles/ejabberd-19.05_1.catalina.bottle.tar.gz](https://homebrew.bintray.com/bottles/ejabberd-19.05_1.catalina.bottle.tar.gz)

ERROR

```
Couldn't start TLS! error -3 tls_error 5
```

Dependencies

```
brew install erlang elixir openssl expat libyaml libiconv libgd sqlite rebar rebar3 automake autoconf 
```

Setup

```
./autogen.sh
export LDFLAGS="-L/usr/local/opt/openssl/lib -L/usr/local/lib -L/usr/local/opt/expat/lib"
export CFLAGS="-I/usr/local/opt/openssl/include/ -I/usr/local/include -I/usr/local/opt/expat/include"
export CPPFLAGS="-I/usr/local/opt/openssl/include/ -I/usr/local/include -I/usr/local/opt/expat/include"
```

Build

```
./configure
make 
make install
```

**Note**: ``--enable-sqlite``, ``--enable-user=`` resulted in error.

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
      - user:admin@localhost
```

Restart server

```
ejabberdctl restart
```

Refresh browser
