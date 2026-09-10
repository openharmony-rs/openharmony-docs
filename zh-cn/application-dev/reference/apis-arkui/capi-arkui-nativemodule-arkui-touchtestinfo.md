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

定义触摸测试信息，用于设置命中测试策略和结果作用的子组件，并获取各子组件的触摸测试结果。

当用户通过[registerNodeEvent](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#registernodeevent)注册了[NODE_ON_CHILD_TOUCH_TEST](capi-native-node-h.md#arkui_nodeeventtype)事件时，开发者才能在事件回调中获取此触摸测试信息结构体。

该结构体支持设置触摸测试策略（取值原则参见[ArkUI_TouchTestStrategy](capi-ui-input-event-h.md#arkui_touchteststrategy)）和命中测试过程中需要作用的子组件ID，并可获取包含各子组件详细测试结果的触摸测试信息项数组。

**起始版本：** 22

**相关模块：** [ArkUI_EventModule](capi-arkui-eventmodule.md)

**所在头文件：** [ui_input_event.h](capi-ui-input-event-h.md)

