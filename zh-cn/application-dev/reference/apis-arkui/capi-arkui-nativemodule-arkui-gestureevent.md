# ArkUI_GestureEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_GestureEvent ArkUI_GestureEvent
```

## 概述

提供手势事件数据类型对象定义，用于在手势事件处理过程中承载和传递手势事件相关数据，支持获取手势事件类型、坐标、时间戳等关键信息；适用于需要处理触摸手势交互的场景，如点击、长按、拖动、缩放等手势识别与响应；开发者可通过相关手势事件接口获取事件信息。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_gesture.h](capi-native-gesture-h.md)

