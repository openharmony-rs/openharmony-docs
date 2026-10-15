# ArkUI_ContextCallback

```c
typedef struct ArkUI_ContextCallback {...} ArkUI_ContextCallback
```

## Overview

Provides an event callback type, which is used to define the callback function and its user-defined data. When an API of this type is called to trigger a callback, the callback is invoked and **userData** is passed as a parameter.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [common_type.h](capi-common-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void* userData | Pointer to the user-defined data, which is passed as a parameter during callback.<br>**Since**: 12 |


### Member functions

| Name | Description |
| -- | -- |
| [void (\*callback)(void* userData)](#callback) | - | Pointer to the callback executed when an event is triggered. This callback does not return any value. When the callback is triggered, the user-defined data pointed to by **userData** is passed as a parameter to execute the custom processing logic. The specific triggering time is defined by the API of this type. |

## Member function description

### callback()

```c
void (*callback)(void* userData)
```

**Description**

Pointer to the callback executed when an event is triggered. This callback does not return any value. When the callback is triggered, the user-defined data pointed to by **userData** is passed as a parameter to execute the custom processing logic. The specific triggering time is defined by the API of this type.

**Since**: 12


