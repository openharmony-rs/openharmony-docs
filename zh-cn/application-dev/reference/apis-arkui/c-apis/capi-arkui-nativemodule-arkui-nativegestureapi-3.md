# ArkUI_NativeGestureAPI_3

```c
typedef struct ArkUI_NativeGestureAPI_3 {...} ArkUI_NativeGestureAPI_3
```

## 概述

定义手势模块接口集合，包含[ArkUI_NativeGestureAPI_1](capi-arkui-nativemodule-arkui-nativegestureapi-1.md)、[ArkUI_NativeGestureAPI_2](capi-arkui-nativemodule-arkui-nativegestureapi-2.md)结构体中的手势接口及新增手势接口。<br>该接口集合支持为ArkUI节点设置并行手势事件回调。回调可从响应链中的冲突手势识别器中选择需要与当前手势并行识别的对象。相关事件数据请参见[ArkUI_ParallelGestureEvent](capi-arkui-nativemodule-arkui-parallelgestureevent.md)。

**起始版本：** 26.0.0

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

**描述：**

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
| ArkUI_ErrorCode | {@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.          <br>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if a parameter error occurs. |


