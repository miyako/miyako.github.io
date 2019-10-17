---
layout: simple
title: Notarization
tags: mac deployment
---

Mac版アプリケーションの仕上げと配付に関する情報をまとめました。

<!--more-->

---

#### Overview

4Dでアプリケーションを作成する場合，インタープリター版（``.4DB``）あるいはコンパイル版（``.4DC``）の**ストラクチャファイル**，あるいは[データベースフォルダー](https://doc.4d.com/4Dv17/4D/17.3/Description-of-4D-files.300-4639958.ja.html)の**パッケージ**（``.4dbase``）を4Dまたは4D Serverとセットで配付し，配付ライセンスをインストールして運用する代わりに，データベースフォルダーや配付ライセンスが組み込まれたカスタムアプリケーションを[**ビルド**](https://doc.4d.com/4Dv17/4D/17.3/Application-builder.300-4639805.ja.html)して配付することができます。

開発|配付|ビルド|ライセンス
:------------|:------|:----:|:----:
Developer Standard | Interpreted Desktop | 不可 | 組込
Developer Standard | SQL Desktop | 不可 | 別途
Developer Standard | Server | 不可 | 別途
Developer Professional | Interpreted Desktop | 不可 | 組込
Developer Professional | SQL Desktop | 不可 | 別途
Developer Professional | Server | 可 | 別途
Developer Professional | Volume Desktop | 必須 | 組込
Developer Professional | OEM Desktop | 必須 | 組込
Developer Professional | OEM Server | 必須 | 組込

アプリケーションをビルドすれば，[名称やアイコンをカスタマイズ](https://doc.4d.com/4Dv17/4D/17.3/Customizing-a-stand-alone-application-icon.300-4639811.ja.html)することができ，[サーバーを選択して接続するまでの手順を簡略化](https://doc.4d.com/4Dv17/4D/17.3/Connecting-to-a-4D-Server-Database.300-4640995.ja.html)したり，[SDIモード](https://doc.4d.com/4Dv17/4D/17.3/SDI-mode-on-Windows.300-4639766.ja.html)や[自動アップグレード](https://doc.4d.com/4Dv17/4D/17/Automatic-updating-of-server-or-single-user-applications.300-3743569.ja.html)などの便利な機能を有効にすることができます。
