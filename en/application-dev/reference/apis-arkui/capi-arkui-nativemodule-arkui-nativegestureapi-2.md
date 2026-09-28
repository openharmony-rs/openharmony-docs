# ArkUI_NativeGestureAPI_2
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=177cf08b41b42ef2a0a1e73e96f1ea583ec5a150 translatedAt=2026-09-20T09:16:57.047Z pushedAt=2026-09-21T12:14:47.284Z -->

```c
typedef struct {...} ArkUI_NativeGestureAPI_2
```

## Overview

Defines a collection of gesture APIs. Based on [ArkUI_NativeGestureAPI_1](capi-arkui-nativemodule-arkui-nativegestureapi-1.md), the capability of setting a gesture interruption event callback is extended, which is used to continue or interrupt a gesture based on the callback result during gesture processing. You can access basic gesture APIs through [gestureApi1](#member-variables) and use [setGestureInterrupterToNode](#setgestureinterruptertonode) to implement complete gesture interruption handling.

**Since**: 18

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

## Summary

### Member Variables

| Name                                       | Description|
|-------------------------------------------| -- |
| [ArkUI_NativeGestureAPI_1](capi-arkui-nativemodule-arkui-nativegestureapi-1.md)* gestureApi1 | Pointer to the **ArkUI_NativeGestureAPI_1** struct.|


### Member Functions

| Name| Description|
| -- | -- |
| [int32_t (\*setGestureInterrupterToNode)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureInterruptResult (\*interrupter)(ArkUI_GestureInterruptInfo* info))](#setgestureinterruptertonode) | Sets the callback function for the gesture interrupt event. |

## Member Function Description

### setGestureInterrupterToNode()

```c
int32_t (*setGestureInterrupterToNode)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureInterruptResult (*interrupter)(ArkUI_GestureInterruptInfo* info))
```

**Description**


Sets the callback function for gesture interruption event. It is applicable to scenarios where you need to decide, based on the current interaction state during gesture recognition, whether the gesture continues to respond or is interrupted, for example, handling gesture response conflicts.

**Parameters**

| Name                      | Description|
|---------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the ArkUI node for which you want to set a gesture interruption callback.|
| void* userData            | Pointer to the user-defined data, which is used to associate the caller's custom context data when setting the gesture interruption callback, for use by the callback to execute its processing logic. If no context needs to be associated, pass a null pointer. |
| [ArkUI_GestureInterruptResult](./capi-native-gesture-h.md#arkui_gestureinterruptresult) (\*interrupter)([ArkUI_GestureInterruptInfo](./capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* info)     | Pointer to the gesture interruption callback function. **info** returns the gesture interruption data. If **interrupter** returns **GESTURE_INTERRUPT_RESULT_CONTINUE**, the gesture recognition process continues, which is suitable for scenarios where the gesture is allowed to continue response. If it returns **GESTURE_INTERRUPT_RESULT_REJECT**, the gesture recognition process is paused, which is suitable for scenarios where other gestures or interactions need to be handled first. If this parameter is set to a null pointer, the callback function is unregistered.<br>**Note:** After the gesture interruption callback function is registered, it will be available in subsequent single-gesture processing. That is, even if you reset the callback function to **nullptr** through **setGestureInterrupterToNode** in the same gesture processing flow or use the [dispose](./capi-arkui-nativemodule-arkui-nativegestureapi-1.md#dispose) API to dispose of the gesture that is about to be triggered, the callback function will still respond when the trigger condition is met. If the object referenced in the callback function may have been released before the callback is triggered, ensure that the object can still be safely accessed while the callback function is being triggered. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |

