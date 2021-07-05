# How to re-sign an xcarchive and export to ipa

## Extract `.app` from `.xcarchive`
```
cp -r ARCHIVE.xcarchive/Products/Applications/APP.app .
```

## Change the bundle identifier
For the app :
```
/usr/libexec/PlistBuddy APP.app/Info.plist -c "Set :CFBundleIdentifier APP_BUNDLE_ID"
```

For each extension :
```
/usr/libexec/PlistBuddy APP.app/PlugIns/EXTENSION.appex/Info.plist -c "Set :CFBundleIdentifier APP_BUNDLE_ID"
```

## Extract entitlements
For the app :
```
codesign -d --entitlements :- APP.app > APP_ENTITLEMENT.plist
```
For each extension :
```
codesign -d --entitlements :- APP.app/PlugIns/EXTENSION.appex > EXTENSION_ENTITLEMENT.plist
```

## Remove code signature
From the app :
```
rm -rf APP.app/Frameworks/*/_CodeSignature
```

From frameworks :
```
rm -rf APP.app/Frameworks/*/_CodeSignature
```

For each extension :
```
rm -rf APP.app/PlugIns/*.appex/_CodeSignature
```

## Replace provisioning profiles
For the app :
```
cp APP_PROFILE.mobileprovision APP.app/embedded.mobileprovision
```

For each extension :
```
cp EXTENSION_PROFILE.mobileprovision APP.app/PlugIns/EXTENSION.appex/embedded.mobileprovision
```
