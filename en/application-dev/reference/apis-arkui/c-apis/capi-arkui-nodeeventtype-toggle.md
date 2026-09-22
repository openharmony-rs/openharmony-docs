# Toggle

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TOGGLE_ON_CHANGE

```c
NODE_TOGGLE_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TOGGLE
```

**Description**

Defines the event triggered when the toggle status changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:** <ul> <li><b>ArkUI_NodeComponentEvent.data[0].i32</b>: toggle status. <b>1</b>: on; <b>0</b>: off.</li> </ul>

**Since**: 12


