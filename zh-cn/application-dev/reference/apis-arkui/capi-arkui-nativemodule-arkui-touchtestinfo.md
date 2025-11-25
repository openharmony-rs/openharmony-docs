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

定义触摸测试信息。

当用户通过[registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)注册了[NODE_ON_CHILD_TOUCH_TEST](capi-native-node-h.md#arkui_nodeeventtype)事件时，才能接收到此事件。触摸测试信息包含触摸测试策略、命中测试过程中需要作用的子组件ID和触摸测试信息项的列表。

**起始版本：** 23

**相关模块：** [ArkUI_EventModule](capi-arkui-eventmodule.md)

**所在头文件：** [ui_input_event.h](capi-ui-input-event-h.md)

