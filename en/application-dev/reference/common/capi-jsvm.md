# JSVM

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:22:50.985Z pushedAt=2026-06-22T03:21:12.896Z -->

## Overview

Provides standard JavaScript engine capabilities. Feature overview: The standard JS engine is a JavaScript code execution engine that strictly complies with the ECMAScript specification. It supports the standard libraries defined by the [ECMAScript specification](https://ecma262.com/) and provides a comprehensive [native API for C++/JS interaction](../../napi/jsvm-introduction.md). It accelerates code execution through JIT compilation, providing applications with secure and efficient JS execution capabilities. The capabilities of the standard JS engine are provided through a stable Application Binary Interface (ABI), namely JavaScript Virtual Machine API (JSVM-API). JSVM-API supports dynamic linking to different versions of the JS engine library, thereby shielding differences between engine APIs. JSVM-API provides capabilities such as engine lifecycle management, JS context management, JS code execution, JS/C++ interoperation, execution environment snapshots, and code cache.<br> Supported platform: arm64 platform.<br> Usage: Link libjsvm.so in the SDK and include the **ark_runtime/jsvm.h** header file in your C++ code.<br>

**Use scenarios:** Implementing cross-language calls between C++ and JavaScript.

**Problem solved:** A standard JavaScript execution environment is provided to ensure code compatibility.

**Benefits:** ECMAScript specification is strictly adhered to, ensuring standardized execution of JavaScript code. Code execution is accelerated through JIT compilation, enhancing application performance. A stable ABI is provided, reducing engine upgrade costs.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

## Files

| Name| Description|
| -- | -- |
| [jsvm.h](capi-jsvm-h.md) | Defines JSVM-APIs. These APIs are used to provide independent, standard, and complete JS engine capabilities, including managing the engine lifecycle, compiling and running JS code, implementing JS/C++ cross-language calls, and taking snapshots.|
| [jsvm_types.h](capi-jsvm-types-h.md) | Defines JSVM-API types. These APIs are used to provide independent, standard, and complete JS engine capabilities, including managing the engine lifecycle, compiling and running JS code, implementing JS/C++ cross-language calls, and taking snapshots.|