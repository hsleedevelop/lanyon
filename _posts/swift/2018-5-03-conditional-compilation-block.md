---
layout: post
title: Conditional Compilation Blocks
description: Conditional Compilation Blocks
category: swift
tags: [swift]
---

[apple-doc](https://developer.apple.com/library/content/documentation/Swift/Conceptual/BuildingCocoaApps/InteractingWithCAPIs.html#//apple_ref/doc/uid/TP40014216-CH8-ID34)

Conditional Compilation Blocks
Swift code and Objective-C code are conditionally compiled in different ways. Swift code can be conditionally compiled using conditional compilation blocks. For example, if you compile the code below using swift -D DEBUG_LOGGING to set the DEBUG_LOGGING conditional compilation flag, the compiler includes the code in the body of the conditional compilation block.

```
#if DEBUG_LOGGING
print("Flag enabled.")
#endif
```

A compilation condition can include the literal true and false values, custom conditional compilation flags (specified using -D <#flag#>), and the platform conditions listed in the table below.

Platform condition | Valid arguments
os() | macOS, iOS, watchOS, tvOS, Linux
arch() | i386, x86_64, arm, arm64
swift() | \>= followed by a version number
canImport() | A module name
targetEnvironment() | simulator

For information about platform conditions, see Conditional Compilation Block in The Swift Programming Language (Swift 4.1).

> NOTE
The arch(arm) platform condition does not return true for ARM 64 devices. The arch(i386) platform condition returns true when code is compiled for the 32–bit iOS simulator.

You can combine compilation conditions using the && and \|\| operators, negate them with the ! operator, and add branches with #elseif and #else compilation directives. You can also nest conditional compilation blocks within other conditional compilation blocks.

```
#if arch(arm) || arch(arm64)
#if swift(>=3.0)
print("Using Swift 3 ARM code")
    #else
    print("Using Swift 2.2 ARM code")
#endif
#elseif arch(x86_64)
print("Using 64-bit x86 code.")
#else
print("Using general code.")
#endif
```

In contrast with condition compilation in the C preprocessor, conditional compilation blocks in Swift must completely surround blocks of code that are self-contained and syntactically valid. This is because all Swift code is syntax checked, even when it is not compiled. However, there is an exception if the compilation condition includes a swift() platform condition: The statements are parsed only if the compiler’s version of Swift matches what is specified in the platform condition. This exception ensures that an older compiler doesn’t attempt to parse syntax introduced in a newer version of Swift.
