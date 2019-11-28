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

Start it

```
/usr/local/sbin/ejabberdctl start
```

Create a user 

```
/usr/local/sbin/ejabberdctl register jimmy.kimmel localhost abc
```

Create another user 

```
/usr/local/sbin/ejabberdctl register jimmy.fallon localhost nbc
```

Login to web admin at [http://localhost:5280/admin/](http://localhost:5280/admin/)
