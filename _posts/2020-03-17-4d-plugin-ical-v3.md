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

For this command to work, the main app (4D) must be signin your app with the ``com.apple.security.personal-information.calendars`` entitlement and have the ``NSCalendarsUsageDescription`` property list key.

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

* ``uid``: read only TEXT
* ``title``: TEXT
* ``notes``: TEXT
* ``color``: LONGINT (see below)
* ``type``: read only TEXT
* ``isEditable``: read only BOOLEAN

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

* ``uid``: read only TEXT
* ``startDate``:  TEXT or DATE
* ``endDate``:  TEXT or DATE
* ``title``:  TEXT
* ``location``: TEXT
* ``url``: TEXT
* ``notes``: TEXT
* ``calendar``: OBJECT
* ``alarms[]``: read only COLLECTION (see below)
* ``attendees[]``: read only COLLECTION (see below)
* ``recurrenceRule``: OBJECT
* ``isAllDay``: BOOLEAN
* ``isDetached``: read only BOOLEAN
* ``occurrence``: read only TEXT
* ``dateStamp``: read only TEXT

**Note**:  ``alarms`` and ``attendees`` can only be updated vis scripting the Calendar app. The properties are read only for this plugin.

Properties of a alarm:

* ``action``: read only TEXT
* ``emailAddress``: read only TEXT
* ``sound``: read only TEXT
* ``url``: read only TEXT
* ``relativeTrigger``: read only REAL
* ``absoluteTrigger``: read only DATE

Properties of a attendee:

* ``status``: read only TEXT
* ``commonName``: read only TEXT
* ``address``: read only TEXT

Properties of a recurrenceRule:

* ``recurrenceInterval``: LONGINT
* ``firstDayOfTheWeek``: LONGINT
* ``recurrenceType``: LONGINT
* ``recurrenceEnd``: OBJECT
* ``recurrenceEnd.usesEndDate``: BOOLEAN
* ``recurrenceEnd.endDate``: DATE
* ``recurrenceEnd.occurrenceCount``: LONGINT
* ``dayOfTheWeek``: write only LONGINT
* ``weekOfTheMonth``: write only LONGINT
* ``daysOfTheWeek[]``: COLLECTION
* ``daysOfTheMonth[]``: COLLECTION
* ``nthWeekDaysOfTheMonth[]``: COLLECTION
* ``monthsOfTheYear[]``: COLLECTION

Properties of a status:

* ``success``: BOOLEAN
* ``error``: OBJECT (if ``success`` is ``false``)
* ``error.code``: LONGINT
* ``error.localizedDescription``: TEXT
* ``error.localizedRecoverySuggestion``: TEXT
