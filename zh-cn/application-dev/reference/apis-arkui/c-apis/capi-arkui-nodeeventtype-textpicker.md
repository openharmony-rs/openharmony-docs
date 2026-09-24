# 滑动选择文本选择器

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_TEXT_PICKER_EVENT_ON_CHANGE

```c
NODE_TEXT_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER
```

**描述：**

定义ARKUI_NODE_TEXT_PICKER列表组件的滚动触摸事件枚举值。<br> 触发该事件的条件：选择文本时触发该事件。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含1个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0...11].i32：表示选中数据的维度。</li> </ul>

**起始版本：** 12

### NODE_TEXT_PICKER_EVENT_ON_SCROLL_STOP

```c
NODE_TEXT_PICKER_EVENT_ON_SCROLL_STOP = 15001
```

**描述：**

定义ARKUI_NODE_TEXT_PICKER列表组件的滚动触摸事件枚举值。<br> 触发该事件的条件：滑动选择文本项停止时触发该事件。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含1个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0...11].i32：表示选中数据的维度。</li> </ul>

**起始版本：** 14


