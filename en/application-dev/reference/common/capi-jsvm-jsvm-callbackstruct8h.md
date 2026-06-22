# JSVM_CallbackStruct*

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:20:49.111Z pushedAt=2026-06-22T06:06:45.669Z -->

```c
typedef JSVM_CallbackStruct* JSVM_Callback
```

## Overview

Defines the pointer types of the native functions provided by user. These functions are exposed to JavaScript via JSVM-API.

**Use scenario:** Implementing JavaScript-callable functions in the native layer, applicable to JSVM extension development scenarios.

**Problem solved:** A standardized function pointer type is defined, making it easier to expose C/C++ functions to the JavaScript environment.

**Features:** A type-safe function pointer definition is provided, supporting interaction between the native and JavaScript layers.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)