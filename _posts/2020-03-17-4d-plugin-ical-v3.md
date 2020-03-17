---
layout: simple
title: iCal v3
tags: plugin mac v17
---

iCal

<!--more-->

[miyako/4d-plugin-ical-v3](https://github.com/miyako/4d-plugin-ical-v3/)

```
status:=iCal_Request_permisson
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
status:=iCal QUERY EVENT (options)
```

<div class="grid">
    <div class="syntax-th cell cell--2">Parameter</div>
    <div class="syntax-th cell cell--2">Type</div>
    <div class="syntax-th cell cell--8">Description</div>
    <div class="syntax-td cell cell--2">options</div>
    <div class="syntax-td cell cell--2">OBJECT</div>
    <div class="syntax-td cell cell--8"></div>     
    <div class="syntax-td cell cell--2">status</div>
    <div class="syntax-td cell cell--2">OBJECT</div>
    <div class="syntax-td cell cell--8"></div>          
</div>

Parameters for ``options``

* ``startDate``:  TEXT
* ``endDate``: TEXT
* ``calendars``: COLLECTION

If ``status.success``, a collection of events will be returned in ``status.events[]``.

```
status:=iCal GET CALENDAR LIST
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
