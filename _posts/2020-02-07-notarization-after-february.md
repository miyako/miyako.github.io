---
layout: simple
title: Notarization after 3rd February 2020
tags: mac deployment
---

Update on app notarisation, following [rules changes](https://developer.apple.com/news/?id=12232019a) starting 3rd February 2020.

<!--more-->

---

#### Overview

Apple has announce that starting this month, [all submitted software must meet the original notarisation prerequisites](https://developer.apple.com/news/?id=12232019a). The [original prerequisites](https://developer.apple.com/news/?id=09032019a) include rules such as:

- The app must have the **Hardened Runtime** capability enabled
- Its components should be signed with the **same Developer ID** as the app
- Its code-signing signature must include a **secure timestamp**
- The app must be built with an **SDK newer than 10.9**
- The app should not include the **com.apple.security.get-task-allow** entitlement set to any variation of ``true``

#### New reality for 4D v17

```json
{
"issues": [
  {
    "severity": "error",
    "code": null,
    "path": "4D.dmg/4D.app/Contents/Plugins/4D InternetCommands.bundle/Contents/MacOS/4D InternetCommands",
    "message": "The binary uses an SDK older than the 10.9 SDK.",
    "docUrl": null,
    "architecture": "i386"
  }
]
}
```

**Workaround**: remove 4D Internet Commands or replace it with a version that uses 10.9 SDK or newer.

- Nothing to do for PHP (i386).

#### New reality for 4D Server v17

- Nothing to do (no plugins are installed by default, notarization is successful).

#### New reality for 4D Volume Desktop v17 R6

```json
{
"issues": [
  {
    "severity": "error",
    "code": null,
    "path": "TEST.dmg/TEST.app/Contents/Resources/php/Mac/php-fcgi-4d",
    "message": "The binary uses an SDK older than the 10.9 SDK.",
    "docUrl": null,
    "architecture": "x86_64"
  }
]
}
```
**Workaround**: remove the ``php`` folder if you don't need it.

