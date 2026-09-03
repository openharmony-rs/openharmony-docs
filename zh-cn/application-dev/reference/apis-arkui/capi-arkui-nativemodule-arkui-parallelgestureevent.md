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

定义并行手势事件。该结构体作为[setGestureParallelTo](capi-arkui-nativemodule-arkui-nativegestureapi-3.md#setgestureparallelto)回调函数的参数传递，包含当前手势识别器、响应链中的冲突手势识别器和用户自定义数据，供回调选择需要与当前手势并行识别的对象。

**起始版本：** 26.0.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_gesture.h](capi-native-gesture-h.md)
