# How to know which shared libraries are used in a binary framework

Use `otool -L` on the binary

From the command line help:
> -L print shared libraries used

Example output of `otool -L MyFramework.framework/MyFramework` :

```no-highlight
@rpath/MyFramework.framework/MyFramework (compatibility version 1.0.0, current version 1.0.0)
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