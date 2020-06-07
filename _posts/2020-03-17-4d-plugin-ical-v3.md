---
layout: simple
title: iCal v3
tags: plugin mac v17
---

iCal (basic read and write).

<!--more-->

[miyako/4d-plugin-ical-v3](https://github.com/miyako/4d-plugin-ical-v3/)

---

#### Changes due to switching from CalendarStore to EventKit SDK:

* removed
  * ``calendar.notes``
  * ``calendar.type`` "IMAP" (``CalCalendarTypeIMAP``)
  * ``calendar.isEditable`` 
  * ``event.dateStamp``
  * ``recurrenceRule.recurrenceEnd.usesEndDate``

* added 

  * ``calendar.immutable``
  * ``calendar.allowsContentModifications``
  * ``calendar.subscribed``
  * ``event.lastModifiedDate``
  * ``event.creationDate``  
  * ``recurrenceRule.weeksOfTheYear`` 
  * ``recurrenceRule.daysOfTheYear`` 
  * ``recurrenceRule.setPositions``

---

```4d
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

```4d
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

```4d
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

```4d
status:=iCal Get default calendar
```

Retutns the default calendar and the list of available ``sources``. You can use one of them to create a new calendar.

```4d
status:=iCal Create calendar(options)
```

``options``: Sepcify a calendar ``title``. By default, a "Local" type is created. You can optinally pass a source title, type or identifier in ``source``. A source identifier or type must match exactly. ``?`` and ``*`` are allowed as [wildcard characters](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Predicates/Articles/pSyntax.html#//apple_ref/doc/uid/TP40001795) for title.

```4d
status:=iCal Set calendar property(options)
```

``options``:  Spepcify a calendar by its ``uid`` or ``title``. Only the ``title`` and ``coler`` are modifiable.

```4d
status:=iCal Get calendar property(options)
status:=iCal Remove calendar(options)
```

 ``options``: Sepcify a calendar by its ``uid`` or ``title``. 

##### calendar properties

* ``uid``: read only TEXT
* ``color``: LONGINT (see below)
* ``type``: read only TEXT (ee below )
* ``title``: TEXT
* ``subscribed``: read only BOOLEAN
* ``immutable``: read only BOOLEAN
* ``allowsContentModifications``: read only BOOLEAN
* ``notes``: TEXT ***Deprecated***  (``3.2.0``)
* ``isEditable``: read only BOOLEAN ***Deprecated***  (``3.2.0``)

**Notes**

* ``uid`` is mapped to [``calendarIdentifier``](https://developer.apple.com/documentation/eventkit/ekcalendar/1507380-calendaridentifier?language=objc)
* ``color`` seems to be "write only" for some calendars.
* ``type`` can be Local, CalDAV, Exchange, Subscription, Birthday. "IMAP" is  ***Deprecated***  (``3.2.0``)

```4d
status:=iCal Set event property(options)
status:=iCal Get event property(options)
status:=iCal Create event(options)
status:=iCal Remove event(options)
```

##### event properties

* ``uid``: read only TEXT 
* ``startDate``:  TEXT or DATE
* ``endDate``:  TEXT or DATE
* ``title``:  TEXT
* ``location``: TEXT
* ``notes``: TEXT
* ``url``: TEXT
* ``calendar``: OBJECT
* ``timeZone``: read only OBJECT
* ``recurrenceRule``: OBJECT
* ``isAllDay``: BOOLEAN
* ``isDetached``: read only BOOLEAN
* ``occurrence``: read only TEXT
* ``creationDate``: read only TEXT
* ``dateStamp``: read only TEXT 
* ``alarms[]``: read only COLLECTION (see below)
* ``attendees[]``: read only COLLECTION (see below)

**Notes**

* ``isAllDay`` is mapped to [``allDay``](https://developer.apple.com/documentation/eventkit/ekevent/1507482-allday?language=objc)
* ``url`` is mapped to [``URL``](https://developer.apple.com/documentation/eventkit/ekcalendaritem/1507265-url?language=objc)
* ``occurrence`` is mapped to [``occurrenceDate``](https://developer.apple.com/documentation/eventkit/ekevent/1507244-occurrencedate?language=objc)
* ``dateStamp`` is mapped to [``lastModifiedDate``](https://developer.apple.com/documentation/eventkit/ekcalendaritem/1507374-lastmodifieddate?language=objc)
* ``alarms`` is currently read-only.

**TODO**: [``addAlarm:``](https://developer.apple.com/documentation/eventkit/ekcalendaritem/1507397-addalarm?language=objc), [``removeAlarm:``](https://developer.apple.com/documentation/eventkit/ekcalendaritem/1507133-removealarm?language=objc)

> it is not possible to add attendees with Event Kit

[attendees](https://developer.apple.com/documentation/eventkit/ekcalendaritem/1507140-attendees?language=objc)

##### alarm properties

* ``action``: read only TEXT
* ``emailAddress``: read only TEXT
* ``sound``: read only TEXT
* ``url``: read only TEXT ***Deprecated***  (``3.2.0``)
* ``relativeTrigger``: read only REAL
* ``absoluteTrigger``: read only DATE

**Notes**

* ``sound`` is mapped to [``soundName``](https://developer.apple.com/documentation/eventkit/ekalarm/1507227-soundname?language=objc)
* ``relativeTrigger`` is mapped to [``relativeOffset``](https://developer.apple.com/documentation/eventkit/ekalarm/1507491-relativeoffset?language=objc)
* ``absoluteTrigger`` is mapped to [``absoluteDate``](https://developer.apple.com/documentation/eventkit/ekalarm/1507486-absolutedate?language=objc)
* ``action`` is mapped to [``type``](https://developer.apple.com/documentation/eventkit/ekalarm/1507242-type?language=objc). It can be Sound, Display, Email, Procedure. 

##### attendee properties

* ``isCurrentUser``: read only BOOL
* ``role``: read only TEXT
* ``type``: read only TEXT
* ``status``: read only TEXT
* ``commonName``: read only TEXT
* ``address``: read only TEXT

**Notes**

* ``isCurrentUser`` is mapped to [``currentUser``](https://developer.apple.com/documentation/eventkit/ekparticipant/1507248-currentuser?language=objc)
* ``role`` is mapped to [``participantRole``](https://developer.apple.com/documentation/eventkit/ekparticipant/1507494-participantrole?language=objc)
* ``type`` is mapped to [``participantRole``](https://developer.apple.com/documentation/eventkit/ekparticipant/1507364-participanttype?language=objc)
* ``status`` is mapped to [``participantStatus``](https://developer.apple.com/documentation/eventkit/ekparticipant/1507533-participantstatus?language=objc)
* ``commonName`` is mapped to [``name``](https://developer.apple.com/documentation/eventkit/ekparticipant/1507480-name?language=objc)
* ``address`` is mapped to [``URL``](https://developer.apple.com/documentation/eventkit/ekparticipant/1507435-url?language=objc)

##### recurrenceRule properties

* ``recurrenceInterval``: LONGINT
* ``firstDayOfTheWeek``: LONGINT
* ``recurrenceType``: LONGINT
* ``recurrenceEnd``: OBJECT
* ``recurrenceEnd.usesEndDate``: read only BOOLEAN ***Deprecated***  (``3.2.0``)
* ``recurrenceEnd.endDate``: DATE
* ``recurrenceEnd.occurrenceCount``: LONGINT
* ``dayOfTheWeek``: LONGINT ***Deprecated***  (``3.2.0``)
* ``weekOfTheMonth``: LONGINT ***Deprecated***  (``3.2.0``)
* ``daysOfTheWeek[]``: COLLECTION of numbers
* ``daysOfTheMonth[]``: COLLECTION of numbers
* ``nthWeekDaysOfTheMonth[]``: read only COLLECTION of objects ***Deprecated***  (``3.2.0``)
* ``monthsOfTheYear[]``: COLLECTION of numbers
* ``weeksOfTheYear[]``: COLLECTION of numbers
* ``daysOfTheYear[]``: COLLECTION of numbers
* ``setPositions[]``: COLLECTION of numbers

##### status properties

* ``success``: BOOLEAN
* ``error``: OBJECT (if ``success`` is ``false``)
* ``error.code``: LONGINT
* ``error.localizedDescription``: TEXT
* ``error.localizedRecoverySuggestion``: TEXT
