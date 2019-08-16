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