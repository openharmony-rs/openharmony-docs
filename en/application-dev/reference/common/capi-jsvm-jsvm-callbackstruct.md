# JSVM_CallbackStruct
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

Provides pointers and data of native callback functions provided by users. These functions are exposed to JavaScript through JSVM APIs.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| void* data | Data of the native callback function provided by users.|


### Member Functions

| Name| Description|
| -- | -- |
| [JSVM_Value(JSVM_CDECL* callback)(JSVM_Env env,JSVM_CallbackInfo info)](#callback) | Pointer to the native callback function provided by users.|

## Member Function Description

### callback()

```
JSVM_Value(JSVM_CDECL* callback)(JSVM_Env env,JSVM_CallbackInfo info)
```

**Description**

Pointer to the native callback function provided by users.
