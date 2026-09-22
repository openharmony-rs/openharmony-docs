# 日历选择器

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_CALENDAR_PICKER_EVENT_ON_CHANGE

```c
NODE_CALENDAR_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CALENDAR_PICKER
```

**描述：**

定义NODE_CALENDAR_PICKER选中日期时触发的事件。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含3个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].u32：选中的年。</li> <li>ArkUI_NodeComponentEvent.data[1].u32：选中的月。</li> <li>ArkUI_NodeComponentEvent.data[2].u32：选中的日。</li> </ul>

**起始版本：** 12


