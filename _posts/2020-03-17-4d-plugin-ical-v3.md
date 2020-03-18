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

* ``startDate``:  TEXT or DATE
* ``endDate``: TEXT or DATE
* ``calendars``: COLLECTION of calendar objects. each object must have a ``uid`` or ``title`` property

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

Properties of a calendar:

* ``uid``: read only
* ``title``: TEXT
* ``notes``: TEXT
* ``color``: LONGINT 
* ``type``: read only
* ``isEditable``: read only

**Note**:  ``color`` seems to be "write only" for some calendars.

```
status:=iCal Set calendar property(options)
status:=iCal Get calendar property(options)
status:=iCal Create calendar(options)
status:=iCal Remove calendar(options)
```

Parameters for ``options``

* ``calendar``: a calendar object. the object must have a ``uid`` (except for creating) or ``title`` property

```
status:=iCal Set event property(options)
status:=iCal Get event property(options)
status:=iCal Create event(options)
status:=iCal Remove event(options)
```

Properties of an event:

* ``uid``: read only
* ``startDate``:  TEXT or DATE
* ``endDate``:  TEXT or DATE
* ``title``:  TEXT
* ``location``: TEXT
* ``url``: TEXT
* ``notes``: TEXT
* ``isAllDay``: BOOLEAN
* ``isDetached``: read only
* ``occurrence``: read only
* ``dateStamp``: read only
