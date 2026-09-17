# 复选框

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_CHECKBOX_EVENT_ON_CHANGE

```c
NODE_CHECKBOX_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX
```

**描述：**

Defines the event triggered when the selected status of the <b>ARKUI_NODE_CHECKBOX</b> component changes.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br><b>ArkUI_NodeComponentEvent.data[0].i32</b><b>1</b>: selected; <b>0</b>: not selected.

**起始版本：** 12


