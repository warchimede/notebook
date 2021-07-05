# How to re-sign an xcarchive and export to ipa

## Extract `.app` to create `.ipa`
```
cp ARCHIVE.xcarchive/Products/Applications/APP_NAME.app .
```

## Extract entitlements
For the app:
```
codesign -d --entitlements :- APP_NAME.app > APP_NAME_ENTITLEMENT.plist
```
For each extension:
```
codesign -d --entitlements :- APP_NAME.app/PlugIns/EXTENSION_NAME.appex > EXTENSION_NAME_ENTITLEMENT.plist
```