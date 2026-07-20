# ArkUI_ParallelGestureEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_ParallelGestureEvent ArkUI_ParallelGestureEvent
```

## 概述

定义并行手势事件。该结构体作为[setGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-3.md#setgestureparallelto)回调函数的参数传递，用于在触发触摸测试时，将开发者自定义手势与响应链上其他组件的手势设置为并行关系的场景。

**起始版本：** 26.0.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_gesture.h](capi-native-gesture-h.md)
