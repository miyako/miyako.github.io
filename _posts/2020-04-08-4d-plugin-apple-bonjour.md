---
layout: simple
title: Bonjour v3
tags: plugin mac network v17
---

Automatic discovery of devices and services on a local network with [Bonjour](https://developer.apple.com/bonjour/).

<!--more-->

[miyako/4d-plugin-apple-bonjour](https://github.com/miyako/4d-plugin-apple-bonjour/)

```
status:=Bonjour Publish(params)
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

Bonjour サービスを公開します。``params``には，下記のプロパティを渡すことができます。

* ``domain``

公開するサービスのドメインを文字列で指定します。デフォルトのドメインを指定するには，空の文字列を渡します。ローカルドメインを指定するには，``local.``を指定します。

* ``type``

ネットワークのタイプを文字列で指定します。サービスのタイプとトランスポートレイヤーの両方を含める必要があります。mDNSレスポンダーがサービスを検出できるように，アンダースコア記号（``_``）をプリフィックスします（例:``_http._tcp.``）。サフィックスのピリオド記号（``.``）は，ドメイン名が絶対指定であることを示すためのものです。

* ``name``

サービスの公開名です。すでに公開されているサービスと重複する場合，実際に公開されるサービス名には連番などが付けられるかもしれません。

命名規則等の詳細は，[Bonjour FAQ](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/NetServices/Articles/faq.html#//apple_ref/doc/uid/TP40008762-SW1)をご覧ください。

* ``includesPeerToPeer``

BluetoothおよびWi-Fiのピア・ツー・ピア交信で公開するには``true``を渡します。デフォルトは``false``です。

Bonjourは，バックグラウンドプロセスでセットアップされます。メソッドのコールバックはありません。ワーカープロセスを起動し，定期的に下記のコマンドで状況をポーリングすることができます。

```
status:=Bonjour Status(params)
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

```
status:=Bonjour Update(params)
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

TXTレコードを更新します。``params``の``data``プロパティに，``stringify``されたJSONオブジェクトを渡してください。``data``は，``1``レベルのオブジェクトで，プロパティ名は自由ですが，値は``base64``エンコードされたBLOBでなければなりません。

```
status:=Bonjour Clear(params)
```

サービスを停止し，すべてのリソースを解放します。なお，アプリケーション終了時には，すべてのサービスが自動的にクリアされます。

```
status:=Bonjour Clear(Discover)
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

指定したドメインでサービスを検出し，アドレスなどの情報を取得します。``params``に渡すことができるプロパティは``Bonjour Publish``と同じですが，``name``は使用されません。

