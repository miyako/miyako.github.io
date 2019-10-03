If access to Camera has been disabled by the user, the system will not ask again for the same app.

For testing, you can ``reset`` the entry for ``Camera`` (case sensitive) with ``tccutil``:

```sh
tccutil reset Camera
```

To request access to Camera, the app (not the plugin) must have 

1. entitlement
1. plist 

You can use my [4d-utility-build-application](https://github.com/miyako/4d-utility-build-application) tool like so:

```
$entitlements["com.apple.security.device.camera"]:=True
```

``NSCameraUsageDescription`` is automatically added by the utility. ``com.apple.security.device.camera`` is ``False`` by default.


<img width="334" alt="スクリーンショット 2019-10-03 12 00 03" src="https://user-images.githubusercontent.com/1725068/66096245-58ac6a80-e5d5-11e9-9557-b6c2d3c0b328.png">

<img width="210" alt="スクリーンショット 2019-10-03 12 03 18" src="https://user-images.githubusercontent.com/1725068/66096398-ce183b00-e5d5-11e9-9b49-1252cd87b68a.png">

<img width="334" alt="スクリーンショット 2019-10-03 12 03 40" src="https://user-images.githubusercontent.com/1725068/66096420-da03fd00-e5d5-11e9-908c-13fc15a48b2a.png">

c.f. [Requesting Authorization for Media Capture on macOS] (https://developer.apple.com/documentation/avfoundation/cameras_and_media_capture/requesting_authorization_for_media_capture_on_macos?language=objc)
