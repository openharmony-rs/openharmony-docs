# 滑动条

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_SLIDER_EVENT_ON_CHANGE

```c
NODE_SLIDER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER
```

**描述：**

Defines the event triggered when the <b>ARKUI_NODE_SLIDER</b> component is dragged or clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:** <ul> <li><b>ArkUI_NodeComponentEvent.data[0].f32</b>: current slider value.</li> <li><b>ArkUI_NodeComponentEvent.data[1].i32</b>: state triggered by the event.</li> </ul>

**起始版本：** 12


