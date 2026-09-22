# ArkUI_NativeGestureAPI_3

```c
typedef struct ArkUI_NativeGestureAPI_3 {...} ArkUI_NativeGestureAPI_3
```

## Overview

Defines a collection of gesture APIs, including gesture APIs in the {@link ArkUI_NativeGestureAPI_1} and<br>{@link ArkUI_NativeGestureAPI_2} structs and new gesture APIs.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [ArkUI_NativeGestureAPI_2*](capi-arkui-nativemodule-arkui-nativegestureapi-2.md) gestureApi2 | Pointer to the **ArkUI_NativeGestureAPI_2** struct.<br>**Since**: 26.0.0 |


### Member functions

| Name | Description |
| -- | -- |
| [ArkUI_ErrorCode (\*setGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (\*parallelGesture)(ArkUI_ParallelGestureEvent* event))](#setgestureparallelto) | Sets the callback function for a parallel gesture event. |

## Member function description

### setGestureParallelTo()

```c
ArkUI_ErrorCode (*setGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (*parallelGesture)(ArkUI_ParallelGestureEvent* event))
```

**Description**

Sets the callback function for a parallel gesture event.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| node | Pointer to the ArkUI node for which you want to set a parallel gesture event callback. |
| userData | Pointer to the user-defined data. The caller must ensure the security of the data lifecycle. |
| parallelGesture | Parallel gesture event. event returns the data of the parallel gesture event.  ParallelGesture returns the pointer to the gesture recognizer that needs parallel recognition. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |


