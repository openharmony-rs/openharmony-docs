# JSVM_CallbackStruct

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:20:49.577Z pushedAt=2026-06-22T03:21:12.859Z -->

```c
typedef struct {...} JSVM_CallbackStruct
```

## Overview

Defines a struct for the pointer and data of the native callbacks provided by the user. These functions are exposed to JavaScript via JSVM-API.

**Usage scenario:** Implementing functions in the native layer that can be invoked by JavaScript, encapsulating C/C++ functions as JavaScript callbacks, and enabling bidirectional interaction between native and JavaScript.

**Features:** Custom data can be passed to callbacks, and standard callback signatures and the foundational infrastructure for cross-language calls are provided.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| void* data | Data of the native callbacks provided by the user.|

### Member Functions

| Name| Description|
| -- | -- |
| [JSVM_Value(JSVM_CDECL* callback)(JSVM_Env env, JSVM_CallbackInfo info)](#callback) | Pointer to the user-provided native callback function. |

## Member Function Description

### callback()

```c
JSVM_Value(JSVM_CDECL* callback)(JSVM_Env env, JSVM_CallbackInfo info)
```

**Description**

Defines a pointer to the native callback provided by users.