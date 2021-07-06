# How to re-sign an xcarchive and export to ipa

## Extract `.app` from `.xcarchive`
```
cp -r ARCHIVE.xcarchive/Products/Applications/APP.app .
```

## Change the bundle identifier
For the app :
```
/usr/libexec/PlistBuddy APP.app/Info.plist -c "set :CFBundleIdentifier APP_BUNDLE_ID"
```

For each extension :
```
/usr/libexec/PlistBuddy APP.app/PlugIns/EXTENSION.appex/Info.plist -c "set :CFBundleIdentifier APP_BUNDLE_ID"
```

## Extract entitlements
For the app :
```
codesign -d --entitlements :- APP.app > APP_ENTITLEMENTS.plist
```

For each extension :
```
codesign -d --entitlements :- APP.app/PlugIns/EXTENSION.appex > EXTENSION_ENTITLEMENTS.plist
```

## Update entitlements data
For the app : 
```
/usr/libexec/PlistBuddy APP_ENTITLEMENT.plist
set :application-identifier TEAM_ID.APP_BUNDLE_ID
set :com.apple.developer.team-identifier TEAM_ID
set :keychain-access-groups:0 JN44M2PH52.fr.francetv.nve.dlptp
save
exit
```

Do the same for each extension.

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

## Sign everything
First, the frameworks :
```
codesign -f -s "Apple Distribution: CERTIFICATE" APP.app/Frameworks/*
```

Then, for each extension :
```
codesign -f -s "Apple Distribution: CERTIFICATE" --entitlements EXTENSION_ENTITLEMENTS.plist APP.app/PlugIns/EXTENSION.appex
```

Finally, for the app :
```
codesign -f -s "Apple Distribution: CERTIFICATE" --entitlements APP_ENTITLEMENTS.plist APP.app
```

## Create new IPA
```
mkdir output
mkdir output/Payload
mv APP.app output/Payload/
cp -r ARCHIVE.xcarchive/SwiftSupport output/
cd output
zip -qr APP.ipa .
```

- https://www.practicallogix.com/how-to-re-sign-an-ios-build-without-xcode/