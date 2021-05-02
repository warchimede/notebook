# Improve build time

[https://github.com/apple/swift/blob/main/docs/CompilerPerformance.md#diagnostic-options](https://github.com/apple/swift/blob/main/docs/CompilerPerformance.md#diagnostic-options)

[https://www.onswiftwings.com/posts/build-time-optimization-part1/](https://www.onswiftwings.com/posts/build-time-optimization-part1/)

-   To display the build time in the Xcode activity viewer, launch this command:  
    `defaults write com.apple.dt.Xcode ShowBuildOperationDuration YES`
-   To get a warning for any function or expression that takes longer than 100ms to type check, add the following flags to `Other Swift Flags`, only for Debug:
`-Xfrontend -warn-long-function-bodies=100`
`-Xfrontend -warn-long-expression-type-checking=100`
-   To get the top slowest file to compile, use the following `Other Swift Flags`:
`-Xfrontend -debug-time-compilation`
-   Set `ONLY_ACTIVE_ARCH` to `YES` for Debug
-   Set `SWIFT_COMPILATION_MODE` to `Incremental` for Debug, and `Whole Module` for Release
-   Set `SWIFT_OPTIMIZATION_LEVEL` to `No Optimization` for Debug, and `Optimize for Speed` for Release
-   Set `DEBUG_INFORMATION_FORMAT` to `DWARF` for Debug, and `DWARF with dSYM` for Release