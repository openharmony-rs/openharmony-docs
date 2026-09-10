# ArkUI_GestureInterruptInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_GestureInterruptInfo ArkUI_GestureInterruptInfo
```

## 概述

定义手势打断事件数据类型，用于向手势打断回调传递手势识别器、响应链手势识别器和触摸识别器等信息。回调可根据这些信息返回继续或拒绝结果。手势打断机制和接口请参见[native_gesture.h](capi-native-gesture-h.md)中的手势打断接口说明。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_gesture.h](capi-native-gesture-h.md)

