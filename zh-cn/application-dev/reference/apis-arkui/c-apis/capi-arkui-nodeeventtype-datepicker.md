# 日期选择器

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_DATE_PICKER_EVENT_ON_DATE_CHANGE

```c
NODE_DATE_PICKER_EVENT_ON_DATE_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER
```

**描述：**

定义ARKUI_NODE_DATE_PICKER列表组件的滚动触摸事件枚举值。<br> 触发该事件的条件：选择日期时触发该事件。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含3个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32：表示选中时间的年。</li> <li>ArkUI_NodeComponentEvent.data[1].i32：表示选中时间的月，取值范围：[0-11]。</li> <li>ArkUI_NodeComponentEvent.data[2].i32：表示选中时间的天。</li> </ul>

**起始版本：** 12


