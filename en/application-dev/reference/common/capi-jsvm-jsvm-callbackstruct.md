# JSVM_CallbackStruct

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:46:58.481Z pushedAt=2026-08-27T06:21:05.288Z -->

```c
typedef struct {...} JSVM_CallbackStruct
```

## Overview

Defines the pointer to the data of the native callbacks provided by the user. These functions are exposed to JavaScript via JSVM-API.

**Use scenario**: Implements functions callable by JavaScript on the native layer, encapsulates C/C++ functions as JavaScript callbacks, and implements bidirectional interaction between native and JavaScript.

**Features**: Supports passing custom data to callback functions, provides a standard callback function signature, and serves as the infrastructure for cross-language invocation.

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