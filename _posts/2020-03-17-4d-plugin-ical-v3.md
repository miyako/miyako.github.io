---
layout: simple
title: iCal v3
tags: plugin mac v17
---

iCal

<!--more-->

[miyako/4d-plugin-ical-v3](https://github.com/miyako/4d-plugin-ical-v3/)

```
status:=iCal_Request_permisson ()
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>          
</div>

```
status:=iCal GET CALENDAR LIST ()
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>          
</div>

If ``status.success``, a collection of objects will be returned in ``status.calendars[]``.
