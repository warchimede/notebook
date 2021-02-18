# How to convert an existing fat framework to a XCFramework using lipo and xcodebuild

## How to create an XCFramework

[https://help.apple.com/xcode/mac/current/#/dev544efab96](https://help.apple.com/xcode/mac/current/#/dev544efab96)

[https://developer.apple.com/wwdc19/416](https://developer.apple.com/wwdc19/416)

Xcode 12.3 :  Building for iOS Simulator, but the linked and embedded framework was built for iOS + iOS Simulator.

Prepare the arm64 framework
```sh
mkdir arm64

mkdir arm64/myFramework.framework

mkdir arm64/myFramework.framework/Modules

mkdir arm64/myFramework.framework/Modules/myFramework.swiftmodule

mkdir arm64/myFramework.framework/Modules/myFramework.swiftmodule/Project

cp vudrmFairPlay.framework/Info.plist arm64/vudrmFairPlay.framework

cp -r vudrmFairPlay.framework/Headers arm64/vudrmFairPlay.framework

cp vudrmFairPlay.framework/Modules/module.modulemap arm64/vudrmFairPlay.framework/Modules

cp vudrmFairPlay.framework/Modules/vudrmFairPlay.swiftmodule/arm64* arm64/vudrmFairPlay.framework/Modules/vudrmFairPlay.swiftmodule

cp vudrmFairPlay.framework/Modules/vudrmFairPlay.swiftmodule/Project/arm64* arm64/vudrmFairPlay.framework/Modules/vudrmFairPlay.swiftmodule/Project
```
Split the fat framework in all its framework slices
```sh
lipo myFramework.framework/vudrmFairPlay -extract arm64 -output arm64/myFramework.framework/myFramework
```
Use xcodebuild to create de XCFramework
```sh
xcodebuild -create-xcframework -framework arm64/vudrmFairPlay.framework -framework x86_64/vudrmFairPlay.framework -output vudrmFairPlay.xcframework
```
On a besoin que de x86_64 et arm64, sinon la commande dit que les definitions sont équivalentes

Make it a script

- en swift
- avec apple argument parser pour bien tester
- pousser sur github

[https://github.com/apple/swift-argument-parser](https://github.com/apple/swift-argument-parser)

[https://blog.cocoapods.org/CocoaPods-1.9.0-beta/](https://blog.cocoapods.org/CocoaPods-1.9.0-beta/)

[https://stackoverflow.com/questions/26971240/how-do-i-run-a-terminal-command-in-a-swift-script-e-g-xcodebuild](https://stackoverflow.com/questions/26971240/how-do-i-run-a-terminal-command-in-a-swift-script-e-g-xcodebuild)

[https://developer.apple.com/documentation/foundation/process](https://developer.apple.com/documentation/foundation/process)