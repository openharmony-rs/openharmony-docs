# JSVM

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:50:08.668Z pushedAt=2026-08-27T06:57:20.105Z -->

## Overview

Provides standard JavaScript engine capabilities. Function overview: The standard JS engine is a JavaScript code execution engine that strictly complies with the ECMAScript specification. It supports the standard libraries defined in the [ECMAScript specification](https://ecma262.com/) and provides a complete set of [native APIs for C++-JS interaction](../../napi/jsvm-introduction.md). It accelerates code execution through JIT compilation, providing apps with secure and efficient JS execution capabilities. The capabilities of the standard JS engine are provided through a stable ABI (Application Binary Interface), namely JSVM-API (JavaScript Virtual Machine API). JSVM-API supports dynamic linking to JS engine libraries of different versions, thereby shielding developers from the differences between engine interfaces. JSVM-API provides capabilities such as engine lifecycle management, JS context management, JS code execution, JS/C++ interoperation, execution environment snapshots, and code cache.

**Platform:** arm64 platform.

**Usage:** Link libjsvm.so in the SDK and include the ark_runtime/jsvm.h header file in C++ code.

**Use scenario:** Scenarios that require cross-language calls between C++ and JavaScript.

**Problem solved:** Provides a standard JavaScript execution environment to ensure code compatibility.

**Benefits:** Strictly complies with the ECMAScript specification to ensure standardized execution of JavaScript code. JIT compilation accelerates code execution and improves app performance. A stable ABI is provided to reduce engine upgrade costs.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

## Files

| Name| Description|
| -- | -- |
| [jsvm.h](capi-jsvm-h.md) | Defines JSVM-APIs. These APIs are used to provide independent, standard, and complete JS engine capabilities, including managing the engine lifecycle, compiling and running JS code, implementing JS/C++ cross-language calls, and taking snapshots.|
| [jsvm_types.h](capi-jsvm-types-h.md) | Defines JSVM-API types. These APIs are used to provide independent, standard, and complete JS engine capabilities, including managing the engine lifecycle, compiling and running JS code, implementing JS/C++ cross-language calls, and taking snapshots.|