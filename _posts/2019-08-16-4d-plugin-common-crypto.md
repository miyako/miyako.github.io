---
layout: simple
title: Common Crypto
tags: plugin text v17
---

Cryptographic hash functions based on OpenSSL.

<!--more-->

[miyako/4d-plugin-common-crypto](https://github.com/miyako/4d-plugin-common-crypto)

---

#### [MD5](https://en.wikipedia.org/wiki/MD5)

```
hash:=MD5 (value;format)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">format</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">hash</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

#### [RIPEMD](https://en.wikipedia.org/wiki/RIPEMD)

```
hash:=RIPEMD160 (value;format)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">format</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">hash</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

#### [SHA-1](https://en.wikipedia.org/wiki/SHA-1)

```
hash:=SHA1 (value;format)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">format</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">hash</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

#### [SHA-2](https://en.wikipedia.org/wiki/SHA-2)

```
hash:=SHA224 (value;format)
hash:=SHA256 (value;format)
hash:=SHA384 (value;format)
hash:=SHA512 (value;format)
hash:=SHA512_224 (value;format)
hash:=SHA512_256 (value;format)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">format</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">hash</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

#### [SHA-3](https://en.wikipedia.org/wiki/SHA-3)

```
hash:=SHA3_224 (value;format)
hash:=SHA3_256 (value;format)
hash:=SHA3_384 (value;format)
hash:=SHA3_512 (value;format)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">format</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">hash</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

#### [HMAC](https://en.wikipedia.org/wiki/HMAC)

```
hash:=HMACMD5 (key;value;format)
hash:=HMACSHA1 (key;value;format)
hash:=HMACSHA224 (key;value;format)
hash:=HMACSHA256 (key;value;format)
hash:=HMACSHA384 (key;value;format)
hash:=HMACSHA512 (key;value;format)
hash:=HMACSHA512_224 (key;value;format)
hash:=HMACSHA512_256 (key;value;format)
hash:=HMACSHA3_224 (key;value;format)
hash:=HMACSHA3_256 (key;value;format)
hash:=HMACSHA3_384 (key;value;format)
hash:=HMACSHA3_512 (key;value;format)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">key</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">format</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">hash</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

#### [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)

```
hash:=AES128 (value;password;operation;mode;format)
hash:=AES192 (value;password;operation;mode;format)
hash:=AES256 (value;password;operation;mode;format)
```

```
hash:=AES128 (value;"";operation;mode;format;key;iv)
hash:=AES192 (value;"";operation;mode;format;key;iv)
hash:=AES256 (value;"";operation;mode;format;key;iv)
```

use either a password or key/iv pair.

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">password</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">operation</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">mode</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">format</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">hash</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

#### [RSA](https://en.wikipedia.org/wiki/RSA_(cryptosystem))

```
hash:=RSASHA1 (value;key;format)
hash:=RSASHA256 (value;key;format)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">key</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">format</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">hash</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

```
ok:=RSAVERIFYSHA1 (value;key;result;format)
ok:=RSAVERIFYSHA256 (value;key;result;format)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">value</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">key</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">result</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div> 
  <div class="syntax-td cell cell--2">format</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">ok</div>
  <div class="syntax-td cell cell--2">LONGINT</div>
  <div class="syntax-td cell cell--8"></div>  
</div>

### Misc

```
timestamp:=Get timestamp
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">timestamp</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div> 
</div>

```
timestring:=Get timestring
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">timestring</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div> 
</div>

```
unixtime:=Get unixtime
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">unixtime</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div> 
</div>

```
pemText:=PEM From P12 (p12;pemBytes;password)
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">p12</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">pemBytes</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>
  <div class="syntax-td cell cell--2">password</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>  
  <div class="syntax-td cell cell--2">pemText</div>
  <div class="syntax-td cell cell--2">TEXT</div>
  <div class="syntax-td cell cell--8"></div>
</div>

effectively the same as ``openssl pkcs12 -in *.p12 -out *.pem -nodes``
