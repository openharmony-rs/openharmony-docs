---
kits: ["ArkTS Kit"]
description: "Describes the ASan (Address-Sanitizer) out-of-bounds access detection capability integrated into DevEco Studio. ASan detects memory safety issues in C/C++ code and displays error stack details and the code lines that cause errors through FaultLog, helping you troubleshoot memory errors in native code."
keywords: ["ASan", "Address-Sanitizer", "memory error detection", "out-of-bounds access", "FaultLog", "DevEco Studio", "C/C++", "stack details"]
doctype: guide
status: active
---

# C/C++ Memory Error Detection

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @eric96-->
<!--Designer: @liuyingying19huawei-->
<!--Tester: @hwu-mc-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=235c2cef2c01aded2d0dcd8f4c12337fcc18fc53 translatedAt=2026-11-09T08:52:17.286Z nl=1 -->

To achieve better performance of C/C++, the compiler and OS (Windows, Linux, and macOS) runtime framework do not perform security detection on memory operations. This is where AddressSanitizer (ASan) comes into the picture. ASan is integrated in DevEco Studio to detect C/C++ out-of-bounds addresses, and display error stack details and problematic code lines through FaultLog.


For details about how to use ASan, see <!--RP1-->[ASan](https://developer.huawei.com/consumer/en/doc/harmonyos-guides-V5/ide-asan-V5)<!--RP1End-->.
