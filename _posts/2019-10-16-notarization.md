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

10.8 Mountain Lion以降，デフォルトの設定は「App Storeと確認済みの開発元からのアプリケーションを許可」です。App Storeではない場所からダウンロードしたアプリは，[Apple Developer Program](https://developer.apple.com) に登録された開発元の有効な**コード署名**が確認できない場合，GateKeeperは起動をブロックします。

10.15 Catalina以降，コード署名に加え，**公証**（[**ノータリゼーション**](https://developer.apple.com/documentation/xcode/notarizing_your_app_before_distribution?language=objc)）が確認できないアプリは，デフォルトで起動を許可しない設定になりました。公証とは，プログラムがマルウェアのように自己を改竄したりしないことを保証するために，Appleが運営している申告・判定・登録システムのことです。GateKeeperは，初回の起動でアプリが公証にパスしたことを証明する電子的なチケット（ステープル）の存在をチェックします。チケットが確認できない場合，Appleのサーバーにアクセスし，そのアプリが公証にパスしたものかどうか，公証データベースに問い合わせます。

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

* [Mac で App を安全に開く](https://support.apple.com/ja-jp/HT202491)

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

Xcodeをインストールした後，すぐに起動しましょう。コマンドラインツール（追加コンポーネント）のインストールが始まるはずです。コマンドラインツールがインストールされてない場合，``xcode-select --install``でダウンロードしてください。

<img width="573" alt="スクリーンショット 2019-11-12 23 49 09" src="https://user-images.githubusercontent.com/1725068/68681678-28c68e80-05a7-11ea-9a01-e1f93b939886.png">

4Dアプリの署名と公証は，Xcodeアプリではなく，コマンドラインツール経由で実施します。Xcodeのコマンドラインツールは，``xcrun``コマンドを介して実行します。``xcrun``はデフォルトの場所にインストールされているXcodeの内部にあるプログラムを実行するようになっています。デフォルトのパスは下記のコマンドラインで確認することができます。

```
xcode-select -p
```

複数のXcodeがインストールされている場合，あるいは標準的ではない場所にXcodeがインストールされている場合，

```
xcode-select --switch <path>
```

ただし，他の開発ツールに影響を与える恐れがあるので，環境変数の``DEVELOPER_DIR``で一時的にパスを変更したほうが無難かもしれません。

#### Developer ID Application Certificate

Xcodeを起動し，アプリケーションメニューの「Preferences」から「Accounts」のページを開きます。Developer IDを入力し，ログインします。

<img width="400" alt="スクリーンショット 2019-10-17 17 00 06" src="https://user-images.githubusercontent.com/1725068/66989622-abbb0d00-f0ff-11e9-88df-0fa4d2669863.png">

「Manage Certificates」をクリックし，画面の左下にある「＋」アイコンをクリックして，「Developer ID Application」および「Developer ID Installer」証明書を作成します。

**注記**: 無料のApple Developer IDでログインしている場合，Developer ID系の証明書は作成できません。「Mac Developer」証明書は作成できますが，これは個人のデバイスでアプリをテストするための証明書であり，アプリを配付する目的では使用できないものです。

<img width="400" alt="スクリーンショット 2019-10-17 17 06 07" src="https://user-images.githubusercontent.com/1725068/66990143-9d212580-f100-11e9-8ecf-df83a1fb2a7a.png">

#### App Specific Password

配付用アプリの公証は，ビルド毎に実行する必要があるので，自動化しておくと便利です。その場合，パスワードの入力を自動化するために，**App用パスワード**を作成しておきます。パスワードは，Apple IDのアカウントページにログインし，「セキュリティ」セクションの「App 用パスワード」の下の「パスワードを生成」をクリックすれば自動的に作成されます。「このパスワードのラベルを入力」には，後で参照できる簡単な文字列（例：``abcde``）を入力します。

生成されたパスワードをコピーし，Macのターミナルを起動して，下記のようなコマンドラインを実行します。


```
xcrun altool --store-password-in-keychain-item <item_name> -u <apple_developer_id> -p <secret_password>
```

うまくいかない場合：

```
security add-generic-password -a <apple_developer_id> -w <secret_password> -s <item_name>
```

これにより，**キーチェーン**にアプリ用のパスワードが保存され，下記のようなコマンドラインでパスワードが参照できるようになります。

```
xcrun altool --notarize-app -u <apple_developer_id> -p "@keychain:<item_name>"
```

これでアプリの署名と公証に必要な準備が整いました！

---

#### Bundle Identifier

4Dのアプリケーションビルダーは，アプリ名から自動的にバンドル識別子を生成します。バンドル識別子に無効な文字列が含まれている場合，アプリはビルドできても，公証に失敗します。心配な場合，ビルドしたアプリのプロパティリストをエディターで開き，標準的なバンドル識別子に変更すると良いでしょう。

#### Application Name

アプリケーション名には，原則的に英数字だけを使用するべきです。前述したように，アプリケーション名はバンドル識別子に組み込まれるので，これは重要です。日本語や記号など，英数字ではない文字をアプリ名に使用したい場合，プロパティリストのBundle name (``CFBundleName``) は英数字で設定し，Bundle display name (``CFBundleDisplayName``) のほうに表示用の名称を設定するようにしてください。

#### xattr

デザインメニューの「アプリケーションビルド」，または``BUILD APPLICATION``コマンドを実行し，カスタムアプリをビルドします。「アプリケーションに署名」のチェックボックスは外しておきます。コマンドでビルドする場合，``SignApplication/MacSignature``を``False``に設定します。

インターネットからダウンロードしたファイルには，URLや日時などの**拡張ファイル属性**が追加されています。また，Finderの「情報を見る」ダイアログでカスタマイズしたアイコン・コメント・タグなども同様です。ファイルやフォルダーに署名を実施するためには，Macの拡張ファイル属性をすべて消去する必要があるので，ビルドしたアプリケーションのパスに対し，下記のコマンドラインを実行します。

```
xattr -cr <path>
```

**注記**: アプリのアイコンをカスタマイズするには，Finderの「情報を見る」ダイアログではなく，ビルドプロジェクトの``ServerIconMacPath`` ``RuntimeVLIconMacPath`` ``ClientMacIconForMacPath``を使用し，``icns``ファイルのパスを指定します。``icns``ファイルを作成するには，必要なサイズの``.png``画像を``.iconset``という拡張子のフォルダーに入れ，下記のコマンドラインを実行します。

```
iconutil -c <path>
```

単一フレームの``icns``画像では，カスタムアイコンが表示されません。``.png``画像は，``sips``でリサイズすることができます。

```
sips -z <pixelsH> <pixelsW> <path>
```

#### Entitlements

アプリのコード署名には，アプリの実行に必要な**エンタイトルメント**が組み込まれることになっています。エンタイトルメントは，セキュリティおよびプライバシーの観点上，特別な保護が必要とされているリソースに対する明示的なアクセスを求めるものです。それには，下記のようなリクエストが含まれます。

* 音声入力信号
* カメラ
* ユーザーの写真ライブラリ
* ユーザーの位置情報
* ユーザーの連絡先情報
* ユーザーのカレンダー情報

詳細は，Apple Developerの[ドキュメント](https://developer.apple.com/documentation/bundleresources/entitlements?language=objc)を参照してください。

**注記**: エンタイトルメントは，自動的にアクセスを付与するものではありません。アクセスを許可するかどうかは，最終的にユーザーが決定します。また，アプリ毎の許可・不許可の設定は，システム環境設定「セキュリティとプライバシー」で変更することができます。

エンタイトルメントは，XML形式のプロパティリスト（``.plist``）で編集します。すべてのエンタイトルメントを請求する場合，下記のようなファイルになります。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>com.apple.security.automation.apple-events</key>
	<true/>
	<key>com.apple.security.cs.allow-dyld-environment-variables</key>
	<true/>
	<key>com.apple.security.cs.allow-jit</key>
	<true/>
	<key>com.apple.security.cs.allow-unsigned-executable-memory</key>
	<true/>
	<key>com.apple.security.cs.debugger</key>
	<true/>
	<key>com.apple.security.cs.disable-executable-page-protection</key>
	<true/>
	<key>com.apple.security.cs.disable-library-validation</key>
	<true/>
	<key>com.apple.security.device.audio-input</key>
	<true/>
	<key>com.apple.security.device.camera</key>
	<true/>
	<key>com.apple.security.get-task-allow</key>
	<true/>
	<key>com.apple.security.personal-information.addressbook</key>
	<true/>
	<key>com.apple.security.personal-information.calendars</key>
	<true/>
	<key>com.apple.security.personal-information.location</key>
	<true/>
	<key>com.apple.security.personal-information.photos-library</key>
	<true/>
</dict>
</plist>
```

XML形式の``.plist``をそのままコード署名に使用することはできません。バイナリ形式の``.plist``に変換する必要があります。ファイル形式を変換するには，下記のようなコマンドラインを実行します。

```
plutil -convert xml1 <path>
```

#### Hardened Runtime

エンタイトルメントを必要とするようなアプリは，マルウェアではないことを保証するため，書き込みが禁止された実行環境（**Hardened Runtime**）で動作することが求められています。

4Dの場合，アプリ本体に加え，``php-fcgi-4d`` ``HelperTool`` ``Updater`` ``InstallTool``といった実行ファイルが組み込まれているため，それぞれに対し，Hardened Runtimeオプションを付けてコード署名を実施する必要があります。

```
codesign --options=runtime --entitlements <path>
```

プラグイン・フレームワーク・ライブラリなど，実行ファイルがロードする個別のファイルにHardened Runtimeオプションを付ける必要はありません。

#### Timestamp

公証アプリは，セキュアなタイムスタンプを付けて署名されていなければなりません。そのためには，インターネットに接続された状態で``codesign``を実行し，下記のオプションを指定する必要があります。

```
codesign --timestamp
```

#### Platform SDK

公証アプリは，macOS 10.9 SDK以降で開発されていなければなりません。4D本体は，この条件をクリアしていますが，個別のプラグイン・フレームワーク・ライブラリはそうではないかもしれません。そのような場合，macOS 10.9 SDK以降で再コンパイルする必要があります。

#### Inside Out

アプリ・プラグイン・フレームワークなどの「バンドル」フォルダーは，再帰的にコード署名を実施することができます。

```
codesign --deep
```

``--deep``オプションは，すでに署名されているリソースの署名は上書きしません。コード署名は，原則的にフォルダー構造の中から外に向かって実施します。4Dの場合，プリインストールされたアプリや実行ファイルにはエンタイトルメントとHardened Runtimeオプションを指定して署名します。プラグイン・フレームワーク・ライブラリなどのリソースは，エンタイトルメントを指定せずにコード署名を実施します。最後に外殻のアプリ本体を署名しますが，このとき``--force``（強制的に署名）オプションを指定してしまうと，内部リソースの署名が無効になってしまうので，すでに署名が済んでいるリソースの外部では``--force``オプションを指定はしないでください。

#### BNDL

4Dプラグインには，歴史的な経緯により，``4DCB``というバンドル識別子（``CFBundlePackageType``）が設定されていました。Appleの公証は，``BNDL`` ``APPL`` ``FMWK``のような標準バンドル識別子でなければ，包括的なチェックを実施しないようです。プラグインのバンドル識別子は，``BNDL``に設定する必要があります。

#### Bundle Name

アプリ・プラグイン・フレームワークなどの「バンドル」の内部には，``Info.plist``という名称のカタログファイルが存在します。このファイルには，バンドルの基本的な情報が辞書形式（キー/値ペア）で書き込まれていますが，``CFBundleName`` ``CFBundleExecutable`` 等のキー値が実際のファイル名と完全に一致しない場合，たとえば小文字の代わりに大文字が使用されている場合，コード署名エラーになります。

```
invalid Info.plist (plist or signature have been modified)
```

#### Identity

コード署名に使用する証明書が署名のアイデンティーとなります。アプリに署名するのであれば，``Developer ID Application:…``証明書，インストーラーに署名するのであれば，``Developer ID Installer:…``証明書をアイデンティーとして使用します。

キーチェーンに登録されている証明書は，下記のコマンドラインでリストアップすることができます。

```
security find-identity -p basic -v
```

#### Archive

公証の条件を満たすような署名を実施した後，Appleの公証サーバーにアプリを送信します。申請するためには，まず，アプリを``.pkg`` ``.dmg`` ``.zip``いずれかの形式で圧縮する必要があります。

* zip

最上位のフォルダー（拡張子``.app``）を残しておく必要があるので，``zip``ではなく，``ditto``を使用します。

```
ditto -c -k --keepParent <src> <dst>
```

``.zip``ファイルにコード署名を実施することはできません。

* dmg

``hdiutil``でディスクイメージを作成することができます。

```
hdiutil create -format UDBZ -plist -srcfolder <src> <dst>
```

``.dmg``ファイルに署名する場合のアイデンティーは``Developer ID Application:…``証明書です。

* pkg

インストーラーを作成する場合，まず，インストールの対象（ペイロード）を入れるための専用フォルダーを用意します。

```
mkdir payload
```

フォルダーを作成したら，ここにアプリを入れます。

```
cp -R <src> <dst>
```

フォルダーにアプリを入れたら，``pkgbuild``でフォルダーの内容を解析し，コンポーネントリストファイル（``component.plist``）を作成します。

```
pkgbuild --analyze --root <payload_path> <component_plist_path>
```

``component.plist``ファイルは，デフォルトで``BundleIsRelocatable``キーが``YES``となっています。これは，すでにアプリがインストールされていれば，インストールを省略するという設定ですが，``YES``に設定されている場合，インストール先を指定することができません。下記のコマンドラインで``NO``に変更します。

```
plutil -replace BundleIsRelocatable -bool NO <component_plist_path>
```

最後に下記の要領で署名付きのインストーラーを作成することができます。

```
pkgbuild --sign <identity>  --root payload --install-location <payload_path> --component-plist <component_plist_path>
```

インストーラーなので，署名のアイデンティーは``Developer ID Installer:…``証明書となります。

**注記**: 後述するように，アプリが公証にパスした後，改めて配付用のディスクイメージまたはインストーラーを作成することになります。したがって，この段階で圧縮ファイルに署名する必要はありません。

#### Notarization

公証サーバーにアプリを送信するには，下記のコマンドラインを実行します。

```
xcrun altool --notarize-app --file <src> --username <username> --password @keychain:altool --primary-bundle-id <product_bundle_id>
```

``username``には，Apple Developer ID（メールアドレス）を指定します。``password``には，アプリ用パスワードを指定しますが，プレーンテキストで渡すのではなく，キーチェーンから参照することが勧められています。パスワードは，Apple IDのアカウントページで作成し，``xcrun altool --store-password-in-keychain-item``でキーチェーンに追加しておきます。

``@keychain:altool``のように記述するのは，キーチェーンが下記のように設定されているためです。

<img width="534" alt="スクリーンショット 2019-10-21 11 43 50" src="https://user-images.githubusercontent.com/1725068/67173100-98a68680-f3f8-11e9-93e7-e0caa57739ae.png">

``primary-bundle-id``は，公証レコードを参照するために設定する任意の識別子です。アプリ自体の識別子と一致している必要はありません。申請のたびに新しい識別子が必要になるので，アプリの識別子に一意の接尾辞を連結したものを発行すると便利です。

送信に成功すると，トラッキングのために使用するUUIDが返されます。UUIDは，公証の経過を追跡したり，ログを閲覧するために使用します。公証は，数分から数十分で完了するはずです。

* 経過を追跡する

```
xcrun altool --notarization-info <uuid> --username <username> --password @keychain:altool
```

* ログを閲覧する

公証が完了している場合，成否に関係なく，前述したコマンドラインから返された情報に``LogFileURL``が含まれています。URLにアクセスすると，JSON形式のログファイルを閲覧することができます。

#### ステープル

ユーザーがアプリをダウンロードした後，初回の起動でアプリが公証にパスしたことを証明する電子的なチケット（ステープル）の存在をチェックします。チケットが確認できない場合，Appleのサーバーにアクセスし，そのアプリが公証にパスしたものかどうか，公証データベースに問い合わせます。

下記のコマンドラインでチケットをアプリに紐付ける（ステープルする）ことができます。アプリが公証にパスした後でなければ，ステープルはできません。紐付けは，ディスクイメージやインストーラーではなく，アプリ自体に対して実行します。コマンドは，インターネットに接続された状態で実行する必要があります。

```
xcrun stapler staple <path>
```

アプリに公証チケットをステープルした後，改めて``ditto``や``pkgbuild``で配付用のファイルを作成します。

これですべての作業が完了です。

#### 補足情報

* [App用パスワード](https://support.apple.com/ja-jp/HT204397)

[appleid.apple.com](https://appleid.apple.com/#!&page=signin)にログインします。

<img width="515" alt="スクリーンショット 2019-11-07 16 50 34" src="https://user-images.githubusercontent.com/1725068/68369989-d9cfc200-017e-11ea-8e2c-22e4c0339ab0.png">

２ファクタ認証のサインインを許可します。

<img width="480" alt="スクリーンショット 2019-11-07 16 52 07" src="https://user-images.githubusercontent.com/1725068/68370104-0daae780-017f-11ea-8655-5f7529fb7c10.png">

<img width="490" alt="スクリーンショット 2019-11-07 16 53 00" src="https://user-images.githubusercontent.com/1725068/68370127-1ac7d680-017f-11ea-947c-5d116a06c14c.png">

<img width="515" alt="スクリーンショット 2019-11-07 16 53 32" src="https://user-images.githubusercontent.com/1725068/68370173-36cb7800-017f-11ea-9d4f-6da0a61722dc.png">

**セキュリティ**に移動します。

<img width="515" alt="スクリーンショット 2019-11-07 16 57 07" src="https://user-images.githubusercontent.com/1725068/68370363-a9d4ee80-017f-11ea-815c-3ea98bdaf336.png">

**パスワードを生成…**をクリックします。

**パスワードのラベル**には任意の英数字（空白はOK，記号はNG）を入力します。

<img width="646" alt="スクリーンショット 2019-11-12 23 57 55" src="https://user-images.githubusercontent.com/1725068/68682309-48aa8200-05a8-11ea-9ff7-accc4de93bc3.png">

App用パスワードは``25``まで作成することができます。

**セキュリティ**の「**編集**」ボタンをクリックすると，App用パスワードの**履歴を表示**することができ，削除することもできます。ラベルは，この画面でパスワードを管理するためのものです。同じラベルを使用しても，毎回，違うパスワードが発行されます。

<img width="515" alt="スクリーンショット 2019-11-07 17 19 32" src="https://user-images.githubusercontent.com/1725068/68371901-0ab1f600-0183-11ea-8130-4cf725a12f6a.png">

App用パスワードは，そのまま``altool``に渡すことができますが，できれば，キーチェーン追加することが勧められています。

Xcode 11であれば，``xcrun altool``でApp用パスワードをキーチェーンに追加することができます。

```
xcrun altool --store-password-in-keychain-item "altool" --username "keisuke.miyako@4d.com" --password "xxxx-xxxx-xxxx-xxxx"
```

**注記**: 旧バージョンの``altool``は，``--store-password-in-keychain-item``オプションをサポートしていません。

``xcrun``から``invalid active developer path``エラーが返される場合，コマンドラインツールのパスが正しく設定されていない可能性があります。

```
xcode-select -p
```

上記を実行して``/Library/Developer/CommandLineTools/usr/bin/xcrun``のようなパスが返される場合，``xcrun``のパスをXcode内部のフォルダーに変更してください。

```
sudo xcode-select --switch /Applications/Xcode.app
```

キーチェーンアクセスで該当パスワードを開きます。**名前**には，コマンドラインに渡した文字列（例：``altool``）が入力されています。この文字列は，App用パスワードのラベルと無関係です。**場所**は，空でも構いません。

名前が``altool``だった場合，コマンドラインにパスワードをそのまま渡す代わりに``"@keychain:altool"``という指定ができるようになります。

```
xcrun altool --notarize-app 
	--file <dmg_path> 
	--username "keisuke.miyako@4d.com"
	--password "@keychain:altool" 
	--primary-bundle-id <primary_bundle_id> 
```

``primary_bundle_id``は，~~過去にアップロードしたことがない，一意の文字列（リバールDNS）でなければなりません。アプリやプラグインのバンドルIDを接頭辞にすることもできますし，まったく違う文字列を使用することもできます。~~任意の文字列を使用することができます。毎回，同じ文字列でも構いません。
