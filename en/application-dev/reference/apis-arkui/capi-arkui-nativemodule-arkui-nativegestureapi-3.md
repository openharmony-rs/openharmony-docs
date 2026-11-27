# ArkUI_NativeGestureAPI_3
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9c92183287fa23162e04874223c3b068eb1f8a4d translatedAt=2026-11-23T07:06:27.545Z pushedAt=2026-11-25T01:13:17.358Z nl=1 -->

```c
typedef struct {...} ArkUI_NativeGestureAPI_3
```

## Overview

Defines a collection of gesture APIs, including gesture APIs in the [ArkUI_NativeGestureAPI_1](capi-arkui-nativemodule-arkui-nativegestureapi-1.md) and [ArkUI_NativeGestureAPI_2](capi-arkui-nativemodule-arkui-nativegestureapi-2.md) structs as well as new gesture APIs. It supports setting parallel gesture event callbacks for ArkUI nodes, and is applicable to interaction scenarios that require parallel gesture recognition.

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_gesture.h](capi-native-gesture-h.md)

## Summary

### Member Variables

| Name                                       | Description|
|-------------------------------------------| -- |
| [ArkUI_NativeGestureAPI_2](capi-arkui-nativemodule-arkui-nativegestureapi-2.md)* gestureApi2 | Pointer to the **ArkUI_NativeGestureAPI_2** struct.|


### Member Functions

| Name| Description|
| -- | -- |
| [ArkUI_ErrorCode (\*setGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (\*parallelGesture)(ArkUI_ParallelGestureEvent* event))](#setgestureparallelto) | Sets the callback function for a parallel gesture event.|

## Member Function Description

### setGestureParallelTo()

```c
ArkUI_ErrorCode (*setGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (*parallelGesture)(ArkUI_ParallelGestureEvent* event))
```

**Description**


Sets the callback function for parallel gesture events. This API applies to scenarios where your custom gesture needs to be processed in parallel with gestures of other components on the response chain.

**Parameters**

| Name                                                             | Description|
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the ArkUI node for which you want to set a parallel gesture event callback.|
| void* userData                                                         | Pointer to the user-defined data, used to pass the caller's custom context information in the parallel gesture event callback. You can pass **nullptr** when no custom context needs to be associated. If a non-null pointer is passed, the caller must ensure the security of the data lifecycle. If the data is released during the callback, the callback execution may be abnormal. |
| ArkUI_GestureRecognizer* (\*parallelGesture)(ArkUI_ParallelGestureEvent* event) | Pointer to the callback function for a parallel gesture event. **event** indicates the parallel gesture event object, which contains the gesture event information when this callback is triggered. **parallelGesture** returns the pointer to the recognizer for the gesture that needs to be recognized parallelly. |

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | Result code.<br>Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>            Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs. |
