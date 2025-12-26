# JSVM_CallbackStruct
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_CallbackStruct
```

## Overview

Defines the pointer to the data of the native callbacks provided by the user. These functions are exposed to JavaScript via JSVM-API.

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
| [JSVM_Value(JSVM_CDECL* callback)(JSVM_Env env,JSVM_CallbackInfo info)](#callback) | Defines a pointer to the native callback provided by users.|

## Member Function Description

### callback()

```c
JSVM_Value(JSVM_CDECL* callback)(JSVM_Env env,JSVM_CallbackInfo info)
```

**Description**

Defines a pointer to the native callback provided by users.
