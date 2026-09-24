# 复选框群组

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_CHECKBOX_GROUP_EVENT_ON_CHANGE

```c
NODE_CHECKBOX_GROUP_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP
```

**描述：**

Defines the callback triggered when the selected status of the <b>ARKUI_NODE_CHECKBOX_GROOUP</b> or checkbox changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <b>ArkUI_StringAsyncEvent.pStr contains two parameters</b> Name: The names of the selected checkboxes; Status: 0: All checkboxes are selected. 1: Some checkboxes are selected. 2: No checkboxes are selected.

**起始版本：** 15


