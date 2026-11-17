---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "介绍DevEco Studio集成的ASan（Address-Sanitizer）地址越界检测能力，为C/C++代码提供内存安全检测，并通过FaultLog展示错误堆栈详情及导致错误的代码行，适用于Native代码内存错误排查场景。"
keywords: [ASan, Address-Sanitizer, 内存错误检测, 地址越界, FaultLog, DevEco Studio, C/C++, 堆栈详情]
doctype: guide
status: active
---

# C/C++内存错误检测

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @eric96-->
<!--Designer: @liuyingying19huawei-->
<!--Tester: @hwu-mc-->
<!--Adviser: @fang-jinxu-->

为追求C/C++的更优性能，编译器和OS(Windows/Linux/Mac)运行框架不会对内存操作进行安全检测。针对该场景，DevEco Studio集成ASan（Address-Sanitizer）为开发者提供面向C/C++的地址越界检测能力，并通过FaultLog展示错误的堆栈详情及导致错误的代码行。


关于ASan的使用说明请参见<!--RP1-->[C/C++内存错误检测](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides-V5/ide-asan-V5)<!--RP1End-->。
