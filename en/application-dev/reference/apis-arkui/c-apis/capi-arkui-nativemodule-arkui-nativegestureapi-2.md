# ArkUI_NativeGestureAPI_2

```c
typedef struct ArkUI_NativeGestureAPI_2 {...} ArkUI_NativeGestureAPI_2
```

## Overview

Defines a collection of gesture APIs. Based on [ArkUI_NativeGestureAPI_1](capi-arkui-nativemodule-arkui-nativegestureapi-1.md), the capability of setting a gesture interruption event callback function is extended, which is used to continue or interrupt a gesture based on the callback result during gesture recognition. You can access basic gesture APIs through **gestureApi1** and use [setGestureInterrupterToNode](capi-arkui-nativemodule-arkui-nativegestureapi-1.md#setgestureinterruptertonode) to handle gesture interruption.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

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
| [int32_t (\*setGestureInterrupterToNode)(ArkUI_NodeHandle node, void* userData,ArkUI_GestureInterruptResult (\*interrupter)(ArkUI_GestureInterruptInfo* info))](#setgestureinterruptertonode) | - | Sets the callback function for gesture interruption events. It is applicable to scenarios where you need to decide, based on the current interaction state during gesture recognition, whether the gesture continues to respond or is interrupted. |

## Member function description

### setGestureInterrupterToNode()

```c
int32_t (*setGestureInterrupterToNode)(ArkUI_NodeHandle node, void* userData,ArkUI_GestureInterruptResult (*interrupter)(ArkUI_GestureInterruptInfo* info))
```

**Description**

Sets the callback function for gesture interruption events. It is applicable to scenarios where you need to decide, based on the current interaction state during gesture recognition, whether the gesture continues to respond or is interrupted.

**Parameters**:

| Parameter | Description |
| -- | -- |
| node | ArkUI node handle for which you want to set a gesture interruption callback function. |
| userData | Pointer to the user-defined data, which is used by the gesture interruption callback function to associate context. If no context needs to be associated, pass a null pointer, in which case the custom context data cannot be obtained in the callback function. If a non-null pointer is passed, ensure that the data can still be safely accessed while the callback function is being triggered. |
| interrupter | Pointer to the gesture interruption callback function. **info** returns the gesture interruption data. If **interrupter** returns **GESTURE_INTERRUPT_RESULT_CONTINUE**, the gesture recognition process continues. If it returns **GESTURE_INTERRUPT_RESULT_REJECT**, the gesture recognition process is paused. If this parameter is set to a null pointer, the callback function is unregistered. <br>**Note:** After the gesture interruption callback function is registered, it will be available in subsequent single-gesture processing. That is, even if you reset the callback function to **nullptr** in the same gesture processing flow or use the **dispose** API to dispose of the gesture that is about to be triggered, the callback function will still respond when the trigger condition is met. If the object referenced in the callback function may have been released before the callback is triggered, ensure that the object can still be safely accessed while the callback function is being triggered. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code. <br>Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful. <br>Returns ARKUI_ERROR_CODE_PARAM_INVALID if a parameter error occurs. |


