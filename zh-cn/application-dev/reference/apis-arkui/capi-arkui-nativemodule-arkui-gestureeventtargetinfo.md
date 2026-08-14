# ArkUI_GestureEventTargetInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_GestureEventTargetInfo ArkUI_GestureEventTargetInfo
```

## 概述

定义手势事件目标信息类型，用于在手势处理过程中查询手势事件目标对象的滚动开始、滚动结束等状态，主要适用于滚动类容器组件。开发者可通过[OH_ArkUI_GetGestureEventTargetInfo](capi-native-gesture-h.md#oh_arkui_getgestureeventtargetinfo)从手势识别器中获取该对象，并通过目标信息查询接口读取目标状态。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_gesture.h](capi-native-gesture-h.md)

