# 容器滑动选择器

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_PICKER_EVENT_ON_CHANGE

```c
NODE_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PICKER
```

**描述：**

定义Picker容器组件中选择某项时触发的事件。<br> 事件回调发生时，事件参数{@link ArkUI_NodeEvent}对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含1个参数：**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32：选中项的值。</li> </ul>

**起始版本：** 23

### NODE_PICKER_EVENT_ON_SCROLL_STOP

```c
NODE_PICKER_EVENT_ON_SCROLL_STOP = 1018001
```

**描述：**

定义Picker容器组件中选择某项且滚动停止时触发的事件。<br> 事件回调发生时，事件参数{@link ArkUI_NodeEvent}对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含1个参数：**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32：选中项的值。</li> </ul>

**起始版本：** 23


