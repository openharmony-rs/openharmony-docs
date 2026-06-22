# JSVM_CallbackInfo__*

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:20:48.753Z pushedAt=2026-06-22T03:21:12.856Z -->

```c
typedef struct JSVM_CallbackInfo__* JSVM_CallbackInfo
```

## Overview

Defines an opaque data type passed to the callback. It can be used to obtain additional information about the context in which the function is called.

**Use scenario:** Implementing JavaScript callback functions in native API development. For example, after registering a callback function in the JSVM module, you can use this type to obtain parameter information and the execution context of the callback invocation.

**Problem solved:** The ability to access the invocation context of JavaScript callback functions from the native layer; the problem that native code cannot obtain callback function parameters and the execution environment.

**Benefits:** The interaction process between the native layer and the JavaScript layer is simplified, allowing you to flexibly access and process parameters passed in from JavaScript within native callback functions, thereby improving the flexibility and development efficiency of native-JavaScript interoperability.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)