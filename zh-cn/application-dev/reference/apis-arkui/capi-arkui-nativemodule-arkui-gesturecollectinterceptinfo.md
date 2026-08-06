# ArkUI_GestureCollectInterceptInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_GestureCollectInterceptInfo ArkUI_GestureCollectInterceptInfo
```

## 概述

定义手势收集拦截信息。在触摸测试收集手势的过程中，该类型用于向拦截回调提供响应链中的手势识别器和触摸识别器，并承载回调设置的手势收集干预结果。相关接口请参见[native_gesture.h](capi-native-gesture-h.md)中的手势收集拦截接口说明。

**起始版本：** 26.0.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

