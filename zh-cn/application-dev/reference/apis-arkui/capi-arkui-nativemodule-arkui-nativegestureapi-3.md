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

## 概述

定义手势模块接口集合。包含[ArkUI_NativeGestureAPI_1](capi-arkui-nativemodule-arkui-nativegestureapi-1.md)、[ArkUI_NativeGestureAPI_2](capi-arkui-nativemodule-arkui-nativegestureapi-2.md)结构体中的手势接口及新增手势接口。

**起始版本：** 26.0.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_gesture.h](capi-native-gesture-h.md)

## 汇总

### 成员变量

| 名称                                        | 描述 |
|-------------------------------------------| -- |
| [ArkUI_NativeGestureAPI_2](capi-arkui-nativemodule-arkui-nativegestureapi-2.md)* gestureApi2 | 指向ArkUI_NativeGestureAPI_2结构体的指针。 |


### 成员函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_ErrorCode (\*setGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (\*parallelGesture)(ArkUI_ParallelGestureEvent* event))](#setgestureparallelto) | 设置并行手势事件的回调函数。 |

## 成员函数说明

### setGestureParallelTo()

```c
ArkUI_ErrorCode (*setGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (*parallelGesture)(ArkUI_ParallelGestureEvent* event))
```

**描述：**


设置并行手势事件的回调函数。

**参数：**

| 参数项                                                              | 描述 |
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 需要设置并行手势事件回调的ArkUI节点指针。 |
| void* userData                                                         | 用户自定义数据。调用者需要确保数据的生命周期安全。 |
| ArkUI_GestureRecognizer* (*parallelGesture)(ArkUI_ParallelGestureEvent* event) | 并行手势事件。event返回并行手势事件的数据；parallelGesture返回需要并行识别的手势识别器指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)表示成功。<br>            返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode)表示参数错误。 |


