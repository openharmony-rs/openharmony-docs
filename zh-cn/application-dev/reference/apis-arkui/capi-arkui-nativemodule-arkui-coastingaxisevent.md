# ArkUI_CoastingAxisEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_CoastingAxisEvent ArkUI_CoastingAxisEvent
```

## 概述

定义惯性滚动轴事件，支持监听触控板双指抛滑产生的衰减滑动过程，适用于在常规轴事件之后处理惯性滚动效果的场景。

当用户在触控板上双指抛滑时，系统根据手指抬起时的速度，按照系统预设的衰减曲线构造惯性滚动轴事件。开发者可以监听此类事件，以便在常规轴事件之后立即处理惯性滚动效果。

仅当满足以下条件时，开发者才能接收到此事件：用户在触控板上双指抛滑，且指针位置下存在通过[registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)注册了[NODE_ON_COASTING_AXIS_EVENT](capi-native-node-h.md#arkui_nodeeventtype)事件的组件。不再需要监听此事件时，应通过[unregisterNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#unregisternodeevent)注销事件监听，避免回调持续触发。

**起始版本：** 22

**相关模块：** [ArkUI_EventModule](capi-arkui-eventmodule.md)

**所在头文件：** [ui_input_event.h](capi-ui-input-event-h.md)

