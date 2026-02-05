# ArkUI_ContextCallback
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @xiang-shouxing; @yangfan229-->
<!--Designer: @piggyguy; @xiang-shouxing; @yangfan229-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_ContextCallback
```

## Overview

Defines the event callback type.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| void* userData | Custom type. The data of the custom type is passed as a parameter during callback.|


### Member Functions

| Name| Description|
| -- | -- |
| [void (\*callback)(void* userData)](#callback) | Event callback.|

## Member Function Description

### callback()

```c
void (*callback)(void* userData)
```

**Description**


Event callback.
