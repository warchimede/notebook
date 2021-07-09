# How to re-sign an `.xcarchive` and export to `.ipa` for App Store submission

I often need to submit for review on App Store Connect app projects coming from external contractors.

I am usually given `.xcarchive`s which bundle identifiers, version numbers and codesigning need to be updated. 😅

Here is a step-by-step guide explaining how I proceed. 🤓

## 0️⃣ Extract the `.app` from the `.xcarchive`

All the necessary work will be done with or within the `.app`, thus it is easier to create a working directory and extract it there right away:

```no-highlight
cp -r ARCHIVE.xcarchive/Products/Applications/APP.app .
```

## 1️⃣ Update the bundle identifier

Now we need to start updating the app's `Info.plist`, so let's use the right tool for the job, aka `PlistBuddy` 🔧 :

```no-highlight
# update the app
/usr/libexec/PlistBuddy APP.app/Info.plist -c "set :CFBundleIdentifier APP_BUNDLE_ID"

# and each extension accordingly
/usr/libexec/PlistBuddy APP.app/PlugIns/EXTENSION.appex/Info.plist -c "set :CFBundleIdentifier EXTENSION_BUNDLE_ID"
```

## 3️⃣ Extract entitlements
For the app :
```no-highlight
codesign -d --entitlements :- APP.app > APP_ENTITLEMENTS.plist
```

For each extension :
```no-highlight
codesign -d --entitlements :- APP.app/PlugIns/EXTENSION.appex > EXTENSION_ENTITLEMENTS.plist
```

## Update entitlements data
For the app : 
```no-highlight
/usr/libexec/PlistBuddy APP_ENTITLEMENT.plist
set :application-identifier TEAM_ID.APP_BUNDLE_ID
set :com.apple.developer.team-identifier TEAM_ID
set :keychain-access-groups:0 TEAM_ID.APP_BUNDLE_ID
save
exit
```

For each extension :
```no-highlight
/usr/libexec/PlistBuddy EXTENSION_ENTITLEMENT.plist
set :application-identifier TEAM_ID.EXTENSION_BUNDLE_ID
set :com.apple.developer.team-identifier TEAM_ID
set :keychain-access-groups:0 TEAM_ID.EXTENSION_BUNDLE_ID
save
exit
```

## Remove code signature
From the app :
```no-highlight
rm -rf APP.app/_CodeSignature
```

From frameworks :
```no-highlight
rm -rf APP.app/Frameworks/*/_CodeSignature
```

For each extension :
```no-highlight
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