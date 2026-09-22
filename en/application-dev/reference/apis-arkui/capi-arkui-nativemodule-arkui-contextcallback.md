# ArkUI_ContextCallback
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=40e7918df96067d113472401a39fcad6e6407d4c translatedAt=2026-09-18T11:29:25.028Z pushedAt=2026-09-20T08:09:59.322Z -->

```c
typedef struct {...} ArkUI_ContextCallback
```

## Overview

Defines an event callback type, which is used to define the callback function and its user-defined data. When an API of this type is called to trigger a callback, the callback is invoked and **userData** is passed as a parameter.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| void* userData | Pointer to the user-defined data, which is passed as a parameter during callback. |


### Member Functions

| Name| Description|
| -- | -- |
| [void (\*callback)(void* userData)](#callback) | Pointer to the callback executed when an event is triggered. The user-defined data pointed to by **userData** is passed when the callback is invoked. |

## Member Function Description

### callback()

```c
void (*callback)(void* userData)
```

**Description**


Pointer to the callback executed when an event is triggered. This callback does not return any value. When the callback is triggered, the user-defined data pointed to by **userData** is passed as a parameter to execute the custom processing logic. The specific triggering time is defined by the API of this type.
