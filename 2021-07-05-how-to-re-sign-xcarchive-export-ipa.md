# How to re-sign an xcarchive and export to ipa

## Extract `.app` from `.xcarchive`
```
cp -r ARCHIVE.xcarchive/Products/Applications/APP.app .
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

