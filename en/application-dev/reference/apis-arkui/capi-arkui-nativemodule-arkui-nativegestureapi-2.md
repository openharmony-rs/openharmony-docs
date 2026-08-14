# ArkUI_NativeGestureAPI_2

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8b7a7d18aa38aad39c3fae4dcbb93ef9e9d5f258 translatedAt=2026-07-17T12:18:51.948Z pushedAt=2026-07-29T02:48:39.428Z -->

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
| [int32_t (\*setGestureInterrupterToNode)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureInterruptResult (\*interrupter)(ArkUI_GestureInterruptInfo* info))](#setgestureinterruptertonode) | Sets the callback for gesture interruption events. |

## Member Function Description

### setGestureInterrupterToNode()

```c
int32_t (*setGestureInterrupterToNode)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureInterruptResult (*interrupter)(ArkUI_GestureInterruptInfo* info))
```

**Description**

Sets the callback for gesture interruption events. This API is applicable to scenarios where the gesture needs to continue responding or be interrupted based on the current interaction state during gesture recognition, for example, handling gesture response conflicts.

**Parameters**

| Name                      | Description|
|---------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the ArkUI node for which you want to set a gesture interruption callback.|
| void* userData            | Pointer to the user-defined data, which is used to associate caller-specific context data when setting the gesture interruption callback. It is used by the callback to execute the processing logic. If no custom context needs to be associated, **nullptr** can be passed. |
| [ArkUI_GestureInterruptResult](./capi-native-gesture-h.md#arkui_gestureinterruptresult) (\*interrupter)([ArkUI_GestureInterruptInfo](./capi-arkui-nativemodule-arkui-gestureinterruptinfo.md)* info)     | Gesture interruption callback. **info** returns the gesture interruption data. If **interrupter** returns **GESTURE_INTERRUPT_RESULT_CONTINUE**, the gesture recognition process continues, which is suitable for the scenario where the gesture is allowed to continue responding. If it returns **GESTURE_INTERRUPT_RESULT_REJECT**, the gesture recognition process is paused, which is suitable for the scenario where other gestures or interactions need to be processed first. If this parameter is set to a null pointer, the callback function is unregistered.<br>Note: After the event interruption callback is registered, it will be available in subsequent single-gesture processing. That is, even if you use the **setGestureInterrupterToNode** API to reset the gesture interruption callback to **nullptr** or use the [dispose](./capi-arkui-nativemodule-arkui-nativegestureapi-1.md#dispose) API to dispose of the gesture that is about to be triggered, the callback will still respond when the trigger condition is met. If the object used in the callback has been released before the callback is triggered, you need to protect the object. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.|