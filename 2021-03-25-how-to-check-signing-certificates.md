# How to check which signing certiface is able to code sign

```no-highlight
security find-identity -vp codesigning
```

Output:

```no-highlight
1) CN5786CB876BC37896V7856V78C63V786CB576V3 "Developer ID Application: THE COMPANY (TEAM64684)"
2) FH783HF304F78H93287HF98723HF789H23G7389H "Apple Development: William Archimede (TEAM64684)"
3) FH0478FH2873HF679G632723F70H378HF237HDH7 "Apple Distribution: THE COMPANY (TEAM64684)"
4) VB0378B87B34N0D98VY65723NV83N834VB794B "iPhone Distribution: THE COMPANY"
     4 valid identities found
```