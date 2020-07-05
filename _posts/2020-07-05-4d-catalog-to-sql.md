---
layout: simple
title: Catalog to SQL
tags: utility v18
---

ストラクチャXMLをSQLステートメントに変換

<!--more-->

[miyako/4d-utility-structure-to-sql-converter-v2](https://github.com/miyako/4d-utility-structure-to-sql-converter-v2/)

### Features

#### Escape reserved names

* The following characters qualify for [escape by brackets](https://doc.4d.com/4Dv18/4D/18/sql-name.300-4650712.en.html): ``!`` ``&`` ``^`` ``#`` ``%``

* Closing brackets (``]``) inside escaped string are duplicated.



The list of [SQL reserved names]() is based on the information displayed in the method editor. 
**Note**: The resource ``STR#:1123`` is incomplete.



