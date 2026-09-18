# 时间选择器

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_TIME_PICKER_EVENT_ON_CHANGE

```c
NODE_TIME_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TIME_PICKER
```

**描述：**

定义ARKUI_NODE_TIME_PICKER列表组件的滚动触摸事件枚举值。<br> 触发该事件的条件：选择时间时触发该事件。 事件回调发生时，事件参数{@link ArkUI_NodeEvent}对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含2个参数：**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32：表示选中时间的时，取值范围：[0-23]。</li><br><li>ArkUI_NodeComponentEvent.data[1].i32：表示选中时间的分，取值范围：[0-59]。</li> </ul>

**起始版本：** 12


