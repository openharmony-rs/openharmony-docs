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

定义手势模块接口集合，包含[ArkUI_NativeGestureAPI_1](capi-arkui-nativemodule-arkui-nativegestureapi-1.md)、[ArkUI_NativeGestureAPI_2](capi-arkui-nativemodule-arkui-nativegestureapi-2.md)结构体中的手势接口及新增手势接口。

该接口集合支持为ArkUI节点设置并行手势事件回调。回调可从响应链中的冲突手势识别器中选择需要与当前手势并行识别的对象。相关事件数据请参见[ArkUI_ParallelGestureEvent](capi-arkui-nativemodule-arkui-parallelgestureevent.md)。

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
| [ArkUI_ErrorCode (\*setGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (\*parallelGesture)(ArkUI_ParallelGestureEvent* event))](#setgestureparallelto) | 设置并行手势事件的回调函数。触发回调时，开发者可从事件提供的冲突手势识别器中返回一个需要与当前手势并行识别的对象。此接口适用于开发者自定义手势与响应链上其他组件手势需要并行处理的场景。 |

## 成员函数说明

### setGestureParallelTo()

```c
ArkUI_ErrorCode (*setGestureParallelTo)(ArkUI_NodeHandle node, void* userData, ArkUI_GestureRecognizer* (*parallelGesture)(ArkUI_ParallelGestureEvent* event))
```

**描述：**


设置并行手势事件的回调函数。触发回调时，开发者可从事件提供的冲突手势识别器中返回一个需要与当前手势并行识别的对象。此接口适用于开发者自定义手势与响应链上其他组件手势需要并行处理的场景。

**参数：**

| 参数项                                                              | 描述 |
|------------------------------------------------------------------| -- |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md) node | 待设置并行手势事件回调函数的ArkUI节点句柄。 |
| void* userData                                                         | 自定义数据，在并行手势事件回调函数中传递开发者自定义上下文信息。不需要关联上下文时可传入nullptr；传入非空指针时，开发者需要确保数据的生命周期安全，若数据在回调过程中被释放可能导致回调执行异常。 |
| ArkUI_GestureRecognizer* (\*parallelGesture)(ArkUI_ParallelGestureEvent* event) | 并行手势事件的回调函数。event为并行手势事件对象，包含触发该回调时的手势事件信息；parallelGesture返回需要并行识别的手势识别器指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) | 返回[ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)表示成功。<br>            返回[ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode)表示参数错误。 |
