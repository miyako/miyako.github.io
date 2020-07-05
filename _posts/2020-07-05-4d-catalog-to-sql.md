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

3 kinds of escape modes are implemented (default=no escape).

1. ``$params.string_quote_mode:="4D"``

    * The following characters qualify for [escape by brackets](https://doc.4d.com/4Dv18/4D/18/sql-name.300-4650712.en.html): ``!`` ``&`` ``^`` ``#`` ``%``

    * Closing brackets (``]``) inside escaped string are duplicated.

    * Names that do not match the pattern ``[a-zA-Z][a-zA-Z0-9_]*`` are escaped.

    * Reserved SQL names are escaped. The list of [SQL reserved names]() is based on the information displayed in the method editor. **Note**: The resource ``STR#:1123`` is incomplete.

2. ``$params.string_quote_mode:="DQ"``

    * Use double quotes, backslash quoted double quotes.

3. ``$params.string_quote_mode:="SQ"``

    * Use single quotes, duplicate quoted single quotes.

#### Table attributes

* Schema definition is exported by default (switch: ``with_schema``) 
* Index definition is exported by default (switch: ``with_index``) 
* Random index name is generated if index has no name (XSLT ``generate-id()``)

#### Field type mapping

Catalog|SQL|Remarks
------------|------|----
1 | BOOLEAN| 
3 | SMALLINT| 16-bit
4 | INT| 32-bit
5 | NUMERIC| 64-bit
6 | REAL| 
7 | FLOAT| 
8 | TIMESTAMP| 
9 | DURATION| 
12 | PICTURE| 
14 | TEXT| outside record or data
15 | INT| 
16 | INT| 
18 | BLOB| 
10 | UUID| @store_as_UUID 
10 | VARCHAR| @limiting_length 
10 | TEXT| 
21 | TEXT| object 

#### Field attributes

* ``@not_null`` and ``@unique`` are always exported
* ``PRIMARY KEY`` is always exported
* ``AUTO_INCREMENT`` is exported by default (switch: ``with_autosequence``) 
* ``AUTO_GENERATE`` is **not** exported by default (switch: ``with_autogenerate``) 
* ``ENABLE REPLICATE`` is **not** exported by default (switch: ``with_replicate``) 
