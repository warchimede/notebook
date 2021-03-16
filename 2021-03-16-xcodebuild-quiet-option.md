# Always use the `-quiet` option with `xcodebuild`

From the `xcodebuild -h` output:

> `-quiet` do not print any output except for warnings and errors

It comes really handy when trying to debug your CI pipelines.

Here's an example of use for testing you project:

```no-highlight
xcodebuild clean test \
   -workspace <workspace> \
   -scheme <scheme> \
   -configuration Debug \
   -destination "<destination>" \
   -derivedDataPath <output_dir> \
   -enableCodeCoverage YES \
   -quiet \
```