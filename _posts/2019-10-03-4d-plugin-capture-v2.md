---
layout: simple
title: Capture
tags: plugin mac userinterface v17
---

Simple video capture based on [AVFoundation](https://developer.apple.com/av-foundation/).

<!--more-->

[miyako/4d-plugin-capture-v2](https://github.com/miyako/4d-plugin-capture-v2)

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

After a system update, ``xcrun`` tasks (``codesign``, ``altool``) might fail with error 

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

properties of ``device``

Property|Type|Description
------------|------|----
uniqueID|TEXT|
modelID|TEXT|
manufacturer|TEXT|
localizedName|TEXT|
connected|BOOLEAN|

```
capture Stop recording
capture Pause recording
capture Resume recording
capture Start recording(option)
```

A capture session must be started beforehand in order to begin recording.

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
file|TEXT|system file path to create QuickTime video

```
capture Start(option)
capture Update(option)
capture Stop
image:=capture Image
```

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

A camera access must be requested per application session, in order to begin video capture.

Property|Type|Description
------------|------|----
window|LONGINT|
x|LONGINT|
y|LONGINT|
width|LONGINT|
height|LONGINT|
flipV|BOOLEAN|
flipH|BOOLEAN|
hidden|BOOLEAN|
device|TEXT|unique ID (optional)

If ``device`` is ommitted, the default camera device will be used.

Only ``x`` ``y`` ``width`` ``height`` ``hidden`` ``flipV`` ``flipH`` can be changed with ``capture Update``.

There can only be one capture session for the application, so passing a different ``window`` will remove the preview layer from the original window and add it to the new window. Likewise, passing a different device ID will force the capture session to be destroyed and recreated.

The preview layer is added to the content view of the window. You should create a session after regular form objects are added to the window, i.e. the first (``-1``) ``On Timer`` event after ``On Load``.

``capture Start`` will force the preview layer to be visible.

``image`` is in JPEG format.

```
status:=capture Request permisson
```

Property|Type|Description
------------|------|----
success|BOOLEAN|
errorMessage|TEXT|
