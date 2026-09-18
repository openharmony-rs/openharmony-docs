# 单选框

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_RADIO_EVENT_ON_CHANGE

```c
NODE_RADIO_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RADIO
```

**描述：**

Defines the event callback function triggered when an object is dragged or clicked by ARKUI_NODE_RADIO. When the event callback occurs, the union type in the {@Link ArkUI_NodeEvent} object is <br>{@Link ArkUI_NodeComponentEvent}. <br>**{@Link ArkUI_NodeComponentEvent} contains one parameter:** <ul> <li>ArkUI_NodeComponentEvent.data[0].i32: option button status.</li> </ul>

**起始版本：** 12


