# How to check which signing certiface is able to codesign

Sadly, having a distribution certificate in your keychain does not always mean it can codesign.

But you can use the following command to make sure it does :

```no-highlight
security find-identity -vp codesigning
```

You will get an output similar to this, showing which certificate is able to codesign :

```no-highlight
1) CN5786CB876BC37896V7856V78C63V786CB576V3 "Developer ID Application: THE COMPANY (TEAM64684)"
2) FH783HF304F78H93287HF98723HF789H23G7389H "Apple Development: William Archimede (TEAM64684)"
3) FH0478FH2873HF679G632723F70H378HF237HDH7 "Apple Distribution: THE COMPANY (TEAM64684)"
4) VB0378B87B34N0D98VY65723NV83N834VB7D294B "iPhone Distribution: THE COMPANY"
     4 valid identities found
```