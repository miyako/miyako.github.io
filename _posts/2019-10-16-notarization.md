---
layout: simple
title: Notarization
tags: mac deployment
---

Mac版アプリケーションの仕上げと配付に関する情報をまとめました。

<!--more-->

---

#### Overview

4Dでアプリを作成する場合，インタープリター版（``.4DB``）あるいはコンパイル版（``.4DC``）の**ストラクチャファイル**，あるいはデータベースフォルダーの**パッケージ**（``.4dbase``）を4Dまたは4D Serverとセットで配付し，配付ライセンスをエンドユーザーのマシンにインストールしてもらう代わりに，データベースフォルダーや配付ライセンスが組み込まれたカスタムアプリを[**ビルド**](https://doc.4d.com/4Dv17/4D/17.3/Application-builder.300-4639805.ja.html)して配付することができます。

開発| 配付 | ビルド | ライセンス
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

10.8 Mountain Lion以降，デフォルトの設定は「App Storeと確認済みの開発元からのアプリケーションを許可」です。これは，[Apple Developer Program](https://developer.apple.com) に登録された開発元の有効な**コード署名**が確認できないアプリは，起動が阻止されることを意味しています。

10.15 Catalina以降，**コード署名**に加え，**公証**（[**ノータリゼーション**](https://developer.apple.com/documentation/xcode/notarizing_your_app_before_distribution?language=objc)）が確認できないアプリは，デフォルトで起動を許可しない設定になりました。公証とは，プログラムがマルウェアのように自己を改竄したりしないことを保証するために，Appleが運営している申告・判定・登録システムのことです。GateKeeperは，初回の起動でアプリが公証にパスしたことを証明する電子的なチケット（ステープル）の存在をチェックします。チケットが確認できない場合，Appleのサーバーにアクセスし，そのアプリが公証にパスしたものかどうか，公証データベースに問い合わせます。

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

4Dおよび4D Serverは署名されていますが，ビルドしたアプリは，4Dから派生した「別アプリ」に該当するため，デベロッパー各自が署名や公証を実施しなければなりません。具体的には，下記のリソースに署名を実施し，公証のチケットを発行してもらうことが必要です。

* ビルドアプリ（本体）
* 4Dに標準で付属しているアプリ（``Updater`` ``InstallTool`` [17r5以降]）
* 4Dに標準で付属している実行ファイル（``php-fcgi-4d`` ``HelperTool`` ``InstallTool`` [17r4以前]）
* その他の実行バンドル（フレームワーク・プラグイン）
* その他の実行ファイル（``.js`` ``.html`` ``.json`` ``LAUNCH EXTERNAL PROCESS``で起動する外部プログラム）

ユーザーは，開発元が信頼できると判断できる場合，``control``キーを押しながらアプリをクリックし，「Mac のセキュリティ設定を一時的に無視して」アプリを起動することができます。また，インターネット経由ではなく，接続した外部ドライブ等からコピーしたファイルであれば，そのまま開くことができます。ですから，**4Dで開発したアプリを配付するために，署名と公証が絶対に必要というわけではありません**。それでも，利便性とユーザーエクスペリンスの観点から，実施することが勧められています。

[Mac で App を安全に開く](https://support.apple.com/ja-jp/HT202491)

#### Prerequisite

署名と公証を実施する前に，下記のものを用意しましょう。

* [macOS 10.14.5以降](https://developer.apple.com/jp/news/?id=04102019a)がインストールされたMac
* [Apple ID の２ファクタ認証](https://support.apple.com/ja-jp/HT204915)
* [App用パスワード](https://support.apple.com/ja-jp/HT204397)
* [Apple Developer Program](https://developer.apple.com/jp/programs/)の有効なメンバーシップ（無料メンバーはNG）
* [Xcode 10以降](https://developer.apple.com/jp/xcode/)
* Developer ID 証明書

Apple Developer Programには，[無料のプログラム](https://developer.apple.com/jp/support/compare-memberships/)も用意されていますが，「App StoreでのApp配信」および「Mac App Store以外でのソフトウェア配信」が特典に含まれていません。無料のメンバーシップでは，Developer ID 証明書の発行ができないためです。署名と公証には，Developer ID 証明書が必要です。

#### Apple ID

Apple IDは，Mac，iOSデバイス，アプリ，オンラインいずれかの方法で作成することができます。Macユーザーであれば，すでに保有しているのではないでしょうか。

* [デバイスの設定時に](https://support.apple.com/ja-jp/HT204316#setup)
* [App Storeで](https://support.apple.com/ja-jp/HT204316#appstore)
* [iTunesで](https://support.apple.com/ja-jp/HT204316#itunes)
* [Webで](https://support.apple.com/ja-jp/HT204316#web)

アプリ開発用に新しいアカウントを作成することもできますが，**２ファクタ認証**を有効にする必要があり，原則的に２台以上のApple機器で同じApple IDを使用していることが想定されているので，個人のApple IDをそのまま使用したほうが簡単かもしれません。

**注記**: Apple機器が１台だけの場合，電話で２ファクタ認証を完了することができます。

#### 2 Factor Authentication

２ファクタ認証は，古典的なユーザー名とパスワードの組み合わせを知っていること（第１ファクター：知識）に加え，当該ユーザーの個人的な電子機器を持っていること（第２ファクター：デバイス）を本人確認の根拠にするという仕組みです。具体的には，６桁の**確認コード**を電話などに送信し，入力させることにより，ユーザーを認証します。Apple IDの場合，２ファクターは任意ですが，Apple Developer IDの場合，２ファクターは必須となっています。

#### Apple Developer Program

Apple IDでログインして，Apple Developer Programに加入の手続きを開始します。２ファクタ認証が有効にされていなければ，このとき設定を済ませるよう案内されます。支払いが完了すると，数時間後に手続き完了の通知メールが送られるはずです。

最新版のmacOSおよびXcodeは，App Storeから入手することができます。古いバージョンのXcodeがアプリケーションフォルダーにインストールされている場合，アプリケーションは上書きされます。以前のXcodeを残しておきたいのであれば，サブフォルダーなど，あらかじめ別の場所に退避してください。

**注記**: [Apple Developer](https://developer.apple.com/download/)にログインすると，開発中（ベータ版）および旧バージョンのソフトウェアがダウンロードできます。

#### Xcode

Xcodeをインストールした後，すぐに起動しましょう。コマンドラインツール（追加コンポーネント）のインストールが始まるはずです。4Dアプリの署名と公証は，Xcodeアプリではなく，コマンドラインツール経由で実施します。Xcodeのコマンドラインツールは，``xcrun``コマンドを介して実行します。``xcrun``はデフォルトの場所にインストールされているXcodeの内部にあるプログラムを実行するようになっています。デフォルトのパスは下記のコマンドラインで確認することができます。

```
xcode-select -p
```

複数のXcodeがインストールされている場合，あるいは標準的ではない場所にXcodeがインストールされている場合，

```
xcode-select --switch {path}
```

ただし，他の開発ツールに影響を与える恐れがあるので，環境変数の``DEVELOPER_DIR``で一時的にパスを変更したほうが無難かもしれません。

#### Developer ID Application Certificate

Xcodeを起動し，アプリケーションメニューの「Preferences」から「Accounts」のページを開きます。Developer IDを入力し，ログインします。

<img width="400" alt="スクリーンショット 2019-10-17 17 00 06" src="https://user-images.githubusercontent.com/1725068/66989622-abbb0d00-f0ff-11e9-88df-0fa4d2669863.png">

「Manage Certificates」をクリックし，画面の左下にある「＋」アイコンをクリックして，「Developer ID Application」および「Developer ID Installer」証明書を作成します。

**注記**: 無料のApple Developer IDでログインしている場合，Developer ID系の証明書は作成できません。「Mac Developer」証明書は作成できますが，これは個人のデバイスでアプリをテストするための証明書であり，アプリを配付する目的では使用できないものです。

<img width="400" alt="スクリーンショット 2019-10-17 17 06 07" src="https://user-images.githubusercontent.com/1725068/66990143-9d212580-f100-11e9-8ecf-df83a1fb2a7a.png">
