# ArkUI_NativeGestureAPI_3

```c
typedef struct ArkUI_NativeGestureAPI_3 {...} ArkUI_NativeGestureAPI_3
```

## 概述

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_gesture.h](capi-native-gesture-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [ArkUI_NativeGestureAPI_2*](capi-arkui-nativemodule-arkui-nativegestureapi-2.md) gestureApi2 | 指向ArkUI_NativeGestureAPI_2结构体的指针。<br>**起始版本：** 26.0.0 |


### 成员函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_ErrorCode (\*setGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (\*parallelGesture)(ArkUI_ParallelGestureEvent* event))](#setgestureparallelto) | Sets the callback function for a parallel gesture event. |

## 成员函数说明

### setGestureParallelTo()

```c
ArkUI_ErrorCode (*setGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (*parallelGesture)(ArkUI_ParallelGestureEvent* event))
```

**描述**

Sets the callback function for a parallel gesture event.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| node | Pointer to the ArkUI node for which you want to set a parallel gesture event callback. |
| userData | Pointer to the user-defined data. The caller must ensure the security of the data lifecycle. |
| parallelGesture | Parallel gesture event. event returns the data of the parallel gesture event. <br>     ParallelGesture returns the pointer to the gesture recognizer that needs parallel recognition. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.          <br>[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs. |


