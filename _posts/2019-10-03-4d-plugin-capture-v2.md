---
layout: simple
title: Capture
tags: plugin mac userinterface v17
---

Simple video capture based on [AVFoundation](https://developer.apple.com/av-foundation/).

<!--more-->

[miyako/4d-plugin-capture-v2](https://github.com/miyako/4d-plugin-capture-v2)

**注記**: プラグインはv17.xでも使用することができますが，サンプルデータベースは**プロジェクトモード**で作成されているため，Ｒバージョンで実行する必要があります。

プレビューエリアを表示したい位置にフォームオブジェクトを配置します。たとえば，透明な四角形オブジェクトを使用することができます。

フォームイベントの``On Load`` ``On Unload`` ``On Timer``を有効にします。必要であれば，``On Resize``も有効にすることができますが，後述する理由により，キャプチャ中のリサイズ処理は非推奨です。

* On Load

カメラデバイスに対するアクセスをリクエストします。

```
Form.status:=capture Request permission 
```

**注記**: 必要なエンタイトルメントとプロパティリストのキーを追加した上でアプリに署名と公証がされていなければ，リクエストはできません。また，ユーザーが同意しなければ，カメラを使用することはできません。カメラが使用できない場合，``status``オブジェクトに理由が返されます。

プレビューエリアを表示したい位置に配置したオブジェクトの座標を取得します。キャプチャはMacの``AVFoundation``テクノロジーを使用しており，プレビューは``CoreAnimation``レイヤーに描画されます。``CoreAnimation``の座標系は，左上ではなく，左下が``0.0``です。そのため，4Dの座標系を反転して計算する必要があります。

```
GET WINDOW RECT($l;$t;$r;$b;Current form window)
			
Form.x:=$left
Form.y:=($b-$t)-($bottom)
Form.width:=$right-$left
Form.height:=$bottom-$top
```

``On Load``では，まだフォームオブジェクトが描画されていません。フォームオブジェクトは，ウィンドウ上のカスタムビューエリアにそれぞれ追加されてゆきます。キャプチャ動画のプレビューレイヤーは，その上に重ねる必要があるので，すべてのフォームオブジェクトが描画された後に追加しなければなりません。ここでは，プロパティだけを設定しておき，タイマーイベントを予約します。

```
Form.flipH:=True
Form.flipV:=False
Form.window:=Current form window
SET TIMER(-1)
```

* On Timer

プレビューエリアをフォームに追加します。指定することができるプロパティは，コマンドの説明を参照してください。

```
SET TIMER(0)
capture Start (Form)
```

Mac版の4Dは，フォームのレンダリングに``CoreAnimation``を使用しており，チェックボックス・ラジオボタン・テキスト入力等のオブジェクトにフォーカスが移動すると，滑らかなアニメーションで表示が更新されるようになっています。プラグインは，外部から新しい``CoreAnimation``レイヤーを追加しているので，すぐには表示が更新されません。強制的にウィンドウを再描画する必要があります。

```
REDRAW WINDOW(Current form window)
```

* On Unload

プラグインは一度に１個のプレビューセッションを１枚のウィンドウにだけ表示するように設計されています。ウィンドウを閉じるときには，セッションを終了するようにしてください。

```
SET TIMER(0)
capture Stop 
```

### Prerequisites

Due to enhanced security requirements from Apple, the app (not the plugin) must be signed with [Camera](https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_security_device_camera?language=objc) and [Hardened Runtime](https://developer.apple.com/documentation/bundleresources/entitlements?language=objc) entitlements. The [NSCameraUsageDescription](https://developer.apple.com/documentation/bundleresources/information_property_list/nscamerausagedescription?language=objc) property list key must also be present.

**Note**: 4D.app itself is signed, but without the above property list entitlements. In order to use the plugin with 4D (interpreted or compiled) you must sign 4D.app with your own Apple Developer certificate.

macOS 10.14以降，プライバシー保護のため，カメラを使用するようなアプリは``Hardened Runtime``および``Camera``の``entitlement``が追加にされた**コード署名**，さらに``NSCameraUsageDescription``という**プロパティリストキー**がなければなりません。これらの条件は，プラグインではなく，アプリ本体に対するものです。4D.appは署名されていますが，必要な``entitlement``が署名に追加されていないため，そのままではカメラを使用することができません。自分のデベロッパー証明書を使用し，署名を上書きする必要があります。

#### Apple Developer ID

In order to sign an app, you need an Apple Developer ID.

**Option 1**: You can convert your regular Apple ID to a **free** Apple Developer ID (you must be over the age of 13). You can create a **Mac Developer** certificate and sign your app for testing on your own computer.

**Option 2**: You may choose to join Apple Developer Program (you must be over the age of 18). You can create a **Developer ID Application** certificate and sign your app for distribution.

<i class="fa fa-external-link" aria-hidden="true"></i> [developer.apple.com](https://developer.apple.com)

コードに署名するためには，**Apple Developer ID**が必要です。通常のApple IDを無料のApple Developer IDに転用した場合，個人のMacで使用できる**Mac Developer**証明書が発行できるようになります。年会費を支払って**Apple Developer Program**に加入すれば，配付用の**Developer ID Application**証明書が発行できるようになります。

#### Two-factor Authentication

Starting February 27, 2019, you must also verify your Apple Developer ID with [Two-factor Authentication](https://developer.apple.com/support/authentication/).

#### App-specific Password

Login to [appleid.apple.com](https://appleid.apple.com/account/manage), move to **Security** and click **Generate Password…**. This is not neccessary for signing your app, but you will need it for **notarisation**.

#### Codesign with Entitlements

You can use the procedure outlined in [4d-utility-build-application](https://github.com/miyako/4d-utility-build-application). The same code is included in the sample structure, method ``TEST``.

コード署名（および公証）を簡単にするための[サンプルコード](https://github.com/miyako/4d-utility-build-application)を公開しています。また，同じコードがサンプルストラクチャにも収録されています。例題に従って必要な``entitlement``でアプリに署名してください。公証が必要ないのであれば，ディスクイメージ作成の手前で中断しても構いません。

**Attention**: After a system update, ``xcrun`` tasks (``codesign``, ``altool``) might fail with error 

```
xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools)
```

You may need to update command line tools to fix it.

```
xcode-select --install
```

### How the plugin requests access

Following Apple guidelines, the plugin calls 

```objc
typedef enum {

    request_permission_unknown = 0,
    request_permission_authorized = 1,
    request_permission_not_determined = 2,
    request_permission_denied = 3,
    request_permission_restricted = 4
    
}request_permission_t;

request_permission_t requestPermission (AVMediaType mediaType) {
    
    if (@available(macOS 10.14, *)) {

        switch ([AVCaptureDevice authorizationStatusForMediaType:mediaType])
        {
            case AVAuthorizationStatusAuthorized:
                request_permission_granted = true;
                return request_permission_authorized;
                break;

            case AVAuthorizationStatusNotDetermined:
                [AVCaptureDevice requestAccessForMediaType:AVMediaTypeVideo completionHandler:^(BOOL granted) {
                    if (granted) {
                        request_permission_granted = true;
                    }
                }];
                return request_permission_not_determined;
                break;

            case AVAuthorizationStatusDenied:
                request_permission_granted = false;
                return request_permission_denied;
                break;
                
            case AVAuthorizationStatusRestricted:
                request_permission_granted = false;
                return request_permission_restricted;
                break;
        }
    }
    
    return request_permission_unknown;
}
```

To avoid immediate termination by the system, the plugin tests for ``NSCameraUsageDescription`` in the main bundle (your app) property list, as well as the ``com.apple.security.device.camera`` entitlement in its bundle resources.

The command ``capture Request permisson`` returns a status object object with an ``errorMessage`` property when ``success`` is ``false``.

When an app requests access for the first time, a prompt is displayed.

<img width="210" alt="スクリーンショット 2019-10-03 12 03 18" src="https://user-images.githubusercontent.com/1725068/66096398-ce183b00-e5d5-11e9-9b49-1252cd87b68a.png">

If the user consents, the app is added to the list of approved apps.

<img width="334" alt="スクリーンショット 2019-10-03 12 03 40" src="https://user-images.githubusercontent.com/1725068/66096420-da03fd00-e5d5-11e9-908c-13fc15a48b2a.png">

If access to Camera granted earlier has been disabled by the user, the system will not ask again for the same app.

For testing, you can ``reset`` the entry for ``Camera`` (case sensitive) with ``tccutil``:

```sh
tccutil reset Camera
```

<img width="334" alt="スクリーンショット 2019-10-03 12 00 03" src="https://user-images.githubusercontent.com/1725068/66096245-58ac6a80-e5d5-11e9-9557-b6c2d3c0b328.png">

---

```
devices:=capture Devices
```

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">devices</div>
  <div class="syntax-td cell cell--2">COLLECTION</div>
  <div class="syntax-td cell cell--8"></div>   
</div>

Returns a collection of video camera devices.

カメラデバイスのリストをコレクション型で返します。

properties of ``device`` object (mac)

Property|Type|Description
------------|------|----
uniqueID|TEXT|pass this to ``capture Start recording`` to specify device other than the default
modelID|TEXT|
manufacturer|TEXT|
localizedName|TEXT|
connected|BOOLEAN|

properties of ``device`` object (windows)

Property|Type|Description
------------|------|----
devicePath|TEXT|pass this to ``capture Start recording`` to specify device other than the default
friendlyName|TEXT|
description|TEXT|

```
capture Stop recording
capture Pause recording
capture Resume recording
capture Start recording(option)
```

A capture session must be started beforehand in order to begin recording.

録画は，すでにキャプチャ（プレビュー）セッションが開始している状態で実行する必要があります。

**Platform remarks**: these 4 recording commands are not available on Windows.

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">option</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>   
</div>

Property|Type|Description
------------|------|----
file|TEXT|system file path to create QuickTime video (``.mov``)

```
capture Start(option)
capture Update(option)
capture Stop
```

A camera access must be requested per application session, in order to begin video capture.

<div class="grid">
  <div class="syntax-th cell cell--2">Parameter</div>
  <div class="syntax-th cell cell--2">Type</div>
  <div class="syntax-th cell cell--8">Description</div>
  <div class="syntax-td cell cell--2">option</div>
  <div class="syntax-td cell cell--2">OBJECT</div>
  <div class="syntax-td cell cell--8"></div>   
  <div class="syntax-td cell cell--2">image</div>
  <div class="syntax-td cell cell--2">PICTURE</div>
  <div class="syntax-td cell cell--8"></div>   
</div>

properties of ``option`` object (windows)

Property|Type|Description
------------|------|----
window|LONGINT|
x|LONGINT|
y|LONGINT|
width|LONGINT|
height|LONGINT|
flipV|BOOLEAN| (optional)
flipH|BOOLEAN| (optional)
hidden|BOOLEAN| (optional)
device|TEXT|unique ID (optional)
force|BOOLEAN|destroy current session instance and create a new one (optional)
file|TEXT|system file path to record video on Windows (``.avi``)  (optional)

If ``device`` is ommitted, the default camera device is assumed.

**Platform remarks**: ``flipV`` ``flipH`` are not available on Windows.

Only ``x`` ``y`` ``width`` ``height`` ``hidden`` ``flipV`` ``flipH`` can be changed with ``capture Update``.

There can only be one capture session for the application, so passing a different ``window`` will remove the preview layer from the original window and add it to the new window. Likewise, passing a different device ID will force the capture session to be destroyed and recreated. You can also force a new session explicitly.

The preview layer is added to the content view of the window. You should create a session after regular form objects are added to the window, i.e. the first (``-1``) ``On Timer`` event after ``On Load``.

Use the ``file`` option on Windows to record video.

The following options are available on Mac only.

Property|Type|Description
------------|------|----
videoCodec|TEXT| ``JPEG`` ``H264`` ``HEVC`` ``AppleProRes422`` ``AppleProRes4444`` (optional)
preset|TEXT| ``low`` ``medium`` ``high`` ``960x540`` ``1280x720`` ``i960x540`` ``i1280x720`` ``320x240`` ``640x480`` ``352x288`` (optional)
quality|REAL| (optional, JPEG and HEIC only)
averageBitRate|LONGINT| (optional, H.264 only)
maxKeyFrameInterval|LONGINT| (optional, H.264 only)
maxKeyFrameIntervalDuration|REAL| (optional, H.264 only)
videoWidth|LONGINT| (optional)
videoHeight|LONGINT| (optional)
maxRecordedDuration|LONGINT| (optional)
maxRecordedFileSize|LONGINT| (optional)

```
image:=capture Image
```
Return a frame picture from an ongoing capture session.

進行中のプレビューセッションからフレームをキャプチャします。

``image`` is a JPEG image on Mac, BMP on Windows.

```
status:=capture Request permisson
```

Property|Type|Description
------------|------|----
success|BOOLEAN|
errorMessage|TEXT|

Request camera access on Mac. The app must be signed with sufficient entitlements and plist keys.

The dialog will not be presented every time. However the app must call this per session in order to access the camera.

アプリケーションにカメラへのアクセス許可を求めます（macOS 10.14以降）。アプリは，必要な``entitlement``で署名されている必要があります（上述）。

アクセスが許可（または拒否）されていれば，ダイアログは表示されませんが，他のコマンドを使用するためにはこのコマンドを実行しなければなりません。
