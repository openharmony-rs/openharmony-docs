# ArkUI_TouchTestInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c++
typedef struct ArkUI_TouchTestInfo ArkUI_TouchTestInfo
```

## 概述

定义触摸测试信息，用于在命中测试过程中获取触摸测试策略、参与命中测试的子组件ID及触摸测试信息项列表，适用于需要在子组件触摸事件中获取命中测试详细信息以自定义命中测试逻辑、优化触摸事件分发与响应的场景。

当用户通过[registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)注册了[NODE_ON_CHILD_TOUCH_TEST](capi-native-node-h.md#arkui_nodeeventtype)事件时，才能接收到此事件。触摸测试信息包含触摸测试策略、命中测试过程中需要参与命中测试的子组件ID和触摸测试信息项的列表。

**起始版本：** 22

**相关模块：** [ArkUI_EventModule](capi-arkui-eventmodule.md)

**所在头文件：** [ui_input_event.h](capi-ui-input-event-h.md)

