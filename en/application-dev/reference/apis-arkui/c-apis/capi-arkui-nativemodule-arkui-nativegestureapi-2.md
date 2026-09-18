# ArkUI_NativeGestureAPI_2

```c
typedef struct ArkUI_NativeGestureAPI_2 {...} ArkUI_NativeGestureAPI_2
```

## Overview

Defines a collection of gesture APIs.

**Since**: 18

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [ArkUI_NativeGestureAPI_1*](capi-arkui-nativemodule-arkui-nativegestureapi-1.md) gestureApi1 | Pointer to the **ArkUI_NativeGestureAPI_1** struct. |


### Member functions

| Name | Description |
| -- | -- |
| [int32_t (\*setGestureInterrupterToNode)(ArkUI_NodeHandle node, void* userData,ArkUI_GestureInterruptResult (\*interrupter)(ArkUI_GestureInterruptInfo* info))](#setgestureinterruptertonode) | Sets the callback for gesture interruption events. |

## Member function description

### setGestureInterrupterToNode()

```c
int32_t (*setGestureInterrupterToNode)(ArkUI_NodeHandle node, void* userData,ArkUI_GestureInterruptResult (*interrupter)(ArkUI_GestureInterruptInfo* info))
```

**Description**

Sets the callback for gesture interruption events.

**Parameters**:

| Parameter | Description |
| -- | -- |
| node | Pointer to the ArkUI node for which you want to set a gesture interruption callback. |
| userData | Pointer to user-defined data. |
| interrupter | Gesture interruption callback to set. <b>info</b> indicates the gesture interruption data. If <b>interrupter</b> returns <b>GESTURE_INTERRUPT_RESULT_CONTINUE</b>, the gesture recognition process proceeds properly. If it returns <b>GESTURE_INTERRUPT_RESULT_REJECT</b>, the gesture recognition process is paused. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code.          <br>Returns {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.<br>    <br>Returns {@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |


