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
