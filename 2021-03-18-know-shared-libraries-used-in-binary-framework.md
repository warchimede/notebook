# How to know which shared libraries are used in a binary framework

```no-highlight
ITMS-90683: Missing Purpose String in Info.plist - Your app's code references one or more APIs that access sensitive user data. The app's Info.plist file should contain a NSBluetoothAlwaysUsageDescription key with a user-facing purpose string explaining clearly and completely why your app needs the data. Starting Spring 2019, all apps submitted to the App Store that access user data are required to include a purpose string. If you're using external libraries or SDKs, they may reference APIs that require a purpose string. While your app might not use these APIs, a purpose string is still required. You can contact the developer of the library or SDK and request they release a version of their code that doesn't contain the APIs.
```
Aren't you tired of receiving such messages when submitting your app to the App Store, especially
when you don't use Bluetooth in your code ?

Well, if you want to contact the developer responsible for this, you have to find which one of your third party dependencies uses `CoreBluetooth.framework`. 🕵🏽‍♂️

## The tool for this quest : `otool` 

`otool` comes with the Xcode toolchain from its command line help :

> -L print shared libraries used

it seems exactly what you are looking for.

Let's use it on `3rdPartySDK.framework`'s binary, the usual suspect :

```no-highlight
otool -L 3rdPartySDK.framework/3rdPartySDK
```

It gives the following output :

```no-highlight
@rpath/3rdPartySDK.framework/3rdPartySDK (compatibility version 1.0.0, current version 1.0.0)
	/usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 904.4.0)
	/System/Library/Frameworks/CFNetwork.framework/CFNetwork (compatibility version 1.0.0, current version 1197.0.0)
	/System/Library/Frameworks/UIKit.framework/UIKit (compatibility version 1.0.0, current version 3987.0.109)
	/System/Library/Frameworks/Foundation.framework/Foundation (compatibility version 300.0.0, current version 1751.108.0)
	/System/Library/Frameworks/MediaAccessibility.framework/MediaAccessibility (compatibility version 1.0.0, current version 62.0.0)
	/System/Library/Frameworks/AudioToolbox.framework/AudioToolbox (compatibility version 1.0.0, current version 1000.0.0)
	/System/Library/Frameworks/CoreBluetooth.framework/CoreBluetooth (compatibility version 1.0.0, current version 1.0.0)
	/System/Library/Frameworks/Security.framework/Security (compatibility version 1.0.0, current version 59754.0.19)
	/System/Library/Frameworks/AVFoundation.framework/AVFoundation (compatibility version 1.0.0, current version 2.0.0)
	/System/Library/Frameworks/MediaPlayer.framework/MediaPlayer (compatibility version 1.0.0, current version 1.0.0)
	/System/Library/Frameworks/Accelerate.framework/Accelerate (compatibility version 1.0.0, current version 4.0.0)
	/System/Library/Frameworks/CoreData.framework/CoreData (compatibility version 1.0.0, current version 1041.0.0)
	/System/Library/Frameworks/CoreText.framework/CoreText (compatibility version 1.0.0, current version 1.0.0)
	/System/Library/Frameworks/QuartzCore.framework/QuartzCore (compatibility version 1.2.0, current version 1.11.0)
	/System/Library/Frameworks/SystemConfiguration.framework/SystemConfiguration (compatibility version 1.0.0, current version 1109.0.4)
	/System/Library/Frameworks/CoreMedia.framework/CoreMedia (compatibility version 1.0.0, current version 1.0.0)
	/usr/lib/libobjc.A.dylib (compatibility version 1.0.0, current version 228.0.0)
	/usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1292.0.0)
	/System/Library/Frameworks/CoreFoundation.framework/CoreFoundation (compatibility version 150.0.0, current version 1751.108.0)
```

Piping with `grep` for a more precise search :

```no-highlight
otool -L 3rdPartySDK.framework/3rdPartySDK | grep CoreBluetooth
```

outputs :

```no-highlight
/System/Library/Frameworks/CoreBluetooth.framework/CoreBluetooth (compatibility version 1.0.0, current version 1.0.0)
```

Well, now you know who to speak to.