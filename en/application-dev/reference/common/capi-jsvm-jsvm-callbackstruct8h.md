# JSVM_CallbackStruct*

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:46:54.362Z pushedAt=2026-08-27T06:23:39.654Z -->

```c
typedef JSVM_CallbackStruct* JSVM_Callback
```

## Overview

Defines the pointer types of the native functions provided by user. These functions are exposed to JavaScript via JSVM-API.

**Usage scenario:** Used when implementing JavaScript-callable functions in the native layer, applicable to JSVM extension development scenarios.

**Problem solved:** Defines a standardized function pointer type to expose C/C++ functions to the JavaScript environment.

**Features:** Provides type-safe function pointer definitions and supports interaction between native and JavaScript.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)