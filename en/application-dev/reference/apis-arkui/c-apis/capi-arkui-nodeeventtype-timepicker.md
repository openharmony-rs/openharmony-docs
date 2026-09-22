# Timepicker

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TIME_PICKER_EVENT_ON_CHANGE

```c
NODE_TIME_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TIME_PICKER
```

**Description**

Defines the event triggered when a time is selected in the <b>ARKUI_NODE_TIME_PICKER</b> component.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters: <ul> <li><b>ArkUI_NodeComponentEvent.data[0].i32</b>: hour of the selected time. Value range: [0-23].</li> <li><b>ArkUI_NodeComponentEvent.data[1].i32</b>: minute of the selected time. Value range: [0-59].</li> </ul>

**Since**: 12


