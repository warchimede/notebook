# Improve app launch/startup time

[https://medium.com/globant/ios-app-launch-time-analysis-and-optimization-a219ee81447c](https://medium.com/globant/ios-app-launch-time-analysis-and-optimization-a219ee81447c)

[https://developer.apple.com/videos/play/wwdc2016/406/](https://developer.apple.com/videos/play/wwdc2016/406/)

To display pre-main() time:
-   set the Build Configuration to Release for the Run section of your scheme
-   set the Environment Variable `DYLD_PRINT_STATISTICS=1` for the Arguments
-   run on device