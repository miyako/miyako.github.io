---
layout: simple
title: Notarization
tags: mac deployment
---

Mac版アプリケーションの仕上げと配付に関する情報をまとめました。

<!--more-->

---

#### Overview

4Dでアプリを作成する場合，インタープリター版（``.4DB``）あるいはコンパイル版（``.4DC``）の**ストラクチャファイル**，あるいは[データベースフォルダー](https://doc.4d.com/4Dv17/4D/17.3/Description-of-4D-files.300-4639958.ja.html)の**パッケージ**（``.4dbase``）を4Dまたは4D Serverとセットで配付し，配付ライセンスをインストールして運用する代わりに，データベースフォルダーや配付ライセンスが組み込まれたカスタムアプリを[**ビルド**](https://doc.4d.com/4Dv17/4D/17.3/Application-builder.300-4639805.ja.html)して配付することができます。

 開発 | 配付 | ビルド | ライセンス
:------------|:------|:----:|:----:
Developer Standard | Interpreted Desktop | 不可 | 組込
Developer Standard | SQL Desktop | 不可 | 別途
Developer Standard | Server | 不可 | 別途
Developer Professional | Interpreted Desktop | 不可 | 組込
Developer Professional | SQL Desktop | 不可 | 別途
Developer Professional | Web Application Server | 不可 | 別途
Developer Professional | Server | 可 | 別途
Developer Professional | Volume Desktop | 必須 | 組込
Developer Professional | OEM Desktop | 必須 | 組込
Developer Professional | OEM Server | 必須 | 組込

アプリをビルドすれば，[名称やアイコンをカスタマイズ](https://doc.4d.com/4Dv17/4D/17.3/Customizing-a-stand-alone-application-icon.300-4639811.ja.html)することができ，[サーバーを選択して接続するまでの手順を簡略化](https://doc.4d.com/4Dv17/4D/17.3/Connecting-to-a-4D-Server-Database.300-4640995.ja.html)したり，[SDIモード](https://doc.4d.com/4Dv17/4D/17.3/SDI-mode-on-Windows.300-4639766.ja.html)（Windows）や[自動アップグレード](https://doc.4d.com/4Dv17/4D/17/Automatic-updating-of-server-or-single-user-applications.300-3743569.ja.html)などの便利な機能を活用することができます。

#### GateKeeper

初期のMac OS Xでは，作成したアプリを``.zip`` ``.pkg`` ``.dmg``などのファイル形式に圧縮し，ユーザーのマシンにダウンロードしてインストールすることができました。Mac OS X 10.7 Lion以降，ユーザーがインターネットからダウンロードしたアプリは，システムに統合された防御機構（[GateKeeper](https://support.apple.com/ja-jp/HT202491)）が初回の起動時にセキュリティのチェックを実施します。GateKeeperの設定は，システム環境設定の「セキュリティとプライバシー（一般）」で確認および変更することができます。

10.8 Mountain Lion以降，デフォルトの設定は「App Storeと確認済みの開発元からのアプリケーションを許可」でした。これは，[Apple Developer Program](https://developer.apple.com) に登録された開発元の有効な**コード署名**が確認できないアプリは，起動を許可しない，という設定です。

10.15 Catalina以降，**コード署名**に加え，**公証**（[**ノータリゼーション**](https://developer.apple.com/documentation/xcode/notarizing_your_app_before_distribution?language=objc)）が確認できないアプリは，デフォルトで起動を許可しない設定になりました。公証とは，プログラムがマルウェアのように自己を改竄したりしないことを保証するために，Appleが運営している申告・判定・登録システムのことです。GateKeeperは，初回の起動でアプリが公証にパスしたことを証明する電子的なチケット（ステープル）の存在をチェックします。チケットが確認できない場合，Appleのサーバーにアクセスし，そのアプリが公証にパスしたものかどうか，チェックします。

**注記**: デベロッパー証明書の盗難による「なりすまし」や，不正に改造されたソフトェアによる被害を食い止めるため，署名や公証を後から取り消すこともできることになっています。

署名や公証が確認できない場合，下記のような警告メッセージが表示されます。

```
…は，開発元を検証できないため開けません。
このアプリケーションにマルウェアが含まれていないことを検証できません。
```

```
…は，壊れているため開けません。ゴミ箱に入れる必要があります。
このファイルは"Safari"により…ダウンロードされました。
```

署名や公証が確認できた場合，下記のようなメッセージが初回の起動時にだけ表示されます。

```
…はインターネットからダウンロードされたアプリケーションです。開いてもよろしいですか?
このファイルは"Safari"により…ダウンロードされました。
```
