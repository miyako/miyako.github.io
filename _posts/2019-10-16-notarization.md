---
layout: simple
title: Notarization
tags: mac deployment
---

Mac版アプリケーションの仕上げと配付に関する情報をまとめました。

<!--more-->

---

#### Overview

4Dでアプリケーションを作成する場合，インタープリター版（``.4DB``）あるいはコンパイル版（``.4DC``）の**ストラクチャファイル**，あるいは[データベースフォルダー](https://doc.4d.com/4Dv17/4D/17.3/Description-of-4D-files.300-4639958.ja.html)の**パッケージ**（``.4dbase``）を4Dまたは4D Serverとセットで配付し，ファイルのダブルクリックあるいはドラッグ＆ドロップ操作で開かせることもできますが，データベースフォルダーを4D Volume Desktopまたは4D Serverに組み込むことにより，オリジナル版のアプリケーションを配付用に作成する，という選択肢もあります。そのようなアプリケーションは，名称やアイコン等をカスタマイズすることができ，(https://doc.4d.com/4Dv17/4D/17/Automatic-updating-of-server-or-single-user-applications.300-3743569.ja.html)[自動アップグレード]をセットアップすることもできます。
