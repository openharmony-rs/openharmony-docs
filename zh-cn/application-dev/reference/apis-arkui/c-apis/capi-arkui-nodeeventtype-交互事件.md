# 交互事件

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_ON_TOUCH_PAD_EVENT

```c
NODE_ON_TOUCH_PAD_EVENT = 38
```

**描述：**

定义上报原始触控板事件时触发的事件。 事件回调触发时，可通过[OH_ArkUI_NodeEvent_GetInputEvent](capi-native-node-h.md#oh_arkui_nodeevent_getinputevent)从[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中获取 [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)对象，输入事件类型为[ARKUI_UIINPUTEVENT_TYPE_TOUCHPAD](capi-ui-input-event-h.md#arkui_uiinputevent_type)。

<!--Device-NODE_ON_TOUCH_PAD_EVENT = 38--><!--Device-NODE_ON_TOUCH_PAD_EVENT = 38-End-->

**起始版本：** 26.1.0

### NODE_ON_TOUCH_PAD_EVENT_INTERCEPT

```c
NODE_ON_TOUCH_PAD_EVENT_INTERCEPT = 39
```

**描述：**

定义触控板事件命中测试的拦截事件。 事件回调触发时，可通过[OH_ArkUI_NodeEvent_GetInputEvent](capi-native-node-h.md#oh_arkui_nodeevent_getinputevent)从[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中获取 [ArkUI_UIInputEvent](capi-arkui-eventmodule-arkui-uiinputevent.md)对象，输入事件类型为[ARKUI_UIINPUTEVENT_TYPE_TOUCHPAD](capi-ui-input-event-h.md#arkui_uiinputevent_type)。使用获取到的输入事件 调用[OH_ArkUI_PointerEvent_SetInterceptHitTestMode](capi-ui-input-event-h.md#oh_arkui_pointerevent_setintercepthittestmode)设置命中测试模式。设置的模式决定组件在当前触控板 事件链中的命中测试行为，不影响触摸、鼠标、轴事件或系统手势事件链。

<!--Device-NODE_ON_TOUCH_PAD_EVENT_INTERCEPT = 39--><!--Device-NODE_ON_TOUCH_PAD_EVENT_INTERCEPT = 39-End-->

**起始版本：** 26.1.0


