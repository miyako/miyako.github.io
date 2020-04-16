---
layout: simple
title: Pseudo Random Number Generator
tags: plugin security v17
---

 [暗号論的擬似乱数生成器](https://ja.wikipedia.org/wiki/暗号論的擬似乱数生成器)プラグイン

<!--more-->

[miyako/4d-plugin-random](https://github.com/miyako/4d-plugin-random/)

```
status:=generate random number({params})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">params</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>      
  <div class="syntax-td cell cell--2">status</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>          
</div>

乱数の生成に成功した場合，``status.success``に``true``が返され，``status.value``に値がセットされます。

``params``は，今のところ未使用です。

```
data:=generate random bytes({params})
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">params</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>      
  <div class="syntax-td cell cell--2">data</div>
  <div class="syntax-td cell cell--2">BLOB</div>
  <div class="syntax-td cell cell--8"></div>          
</div>

``params.size``で指定したバイト数のランダムデータを返します。失敗した場合，BLOBのサイズは``0``です。サイズを省略した場合，``4``バイト（倍長整数）のデータを返します。


#### アルゴリズム

macOSでは，[``SecRandomCopyBytes``](https://developer.apple.com/documentation/security/1399291-secrandomcopybytes?language=objc)をコールしています（``kSecRandomDefault``）。ドキュメントには，**暗号論的擬似乱数**が返されると明記されています。

**論考**

<i class="fa fa-external-link" aria-hidden="true"></i> [https://forums.developer.apple.com/thread/96907](https://forums.developer.apple.com/thread/96907)

Windowsでは，[``BCryptGenRandom``](https://docs.microsoft.com/ja-jp/windows/win32/api/bcrypt/nf-bcrypt-bcryptgenrandom)をコールしています（``BCRYPT_RNG_ALGORITHM``）。ドキュメントには直接的な言及がありませんが，先代APIの[``CryptGenRandom``](https://docs.microsoft.com/ja-jp/windows/win32/api/wincrypt/nf-wincrypt-cryptgenrandom)のページで**暗号論的擬似乱数**が返されると明記されています。
