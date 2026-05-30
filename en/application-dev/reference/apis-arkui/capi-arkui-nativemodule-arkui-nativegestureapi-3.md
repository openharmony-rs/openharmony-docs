# ArkUI_NativeGestureAPI_3
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_NativeGestureAPI_3
```

## Overview

Defines a collection of gesture APIs, including gesture APIs in the [ArkUI_NativeGestureAPI_1](capi-arkui-nativemodule-arkui-nativegestureapi-1.md) and [ArkUI_NativeGestureAPI_2](capi-arkui-nativemodule-arkui-nativegestureapi-2.md) structs and new gesture APIs.

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


Sets the callback function for a parallel gesture event.

**Parameters**

| Name                                                             | Description|
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | Pointer to the ArkUI node for which you want to set a parallel gesture event callback.|
| void* userData                                                         | Pointer to the user-defined data. The caller must ensure the security of the data lifecycle.|
| ArkUI_GestureRecognizer* (*parallelGesture)(ArkUI_ParallelGestureEvent* event) | Pointer to the parallel gesture event. **event** returns the data of the parallel gesture event. **parallelGesture** returns the pointer to the recognizer for the gesture that needs to be recognized parallelly.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>            [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|
