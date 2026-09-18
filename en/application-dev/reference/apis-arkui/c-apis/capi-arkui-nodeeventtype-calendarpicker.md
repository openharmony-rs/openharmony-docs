# Calendarpicker

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_CALENDAR_PICKER_EVENT_ON_CHANGE

```c
NODE_CALENDAR_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CALENDAR_PICKER
```

**Description**

Defines the event triggered when a date is selected in the <b>NODE_CALENDAR_PICKER</b>.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br><ul><br><li><b>ArkUI_NodeComponent.data[0].u32</b>: year of the selected date.</li><br><li><b>ArkUI_NodeComponent.data[1].u32</b>: month of the selected date.</li><br><li><b>ArkUI_NodeComponent.data[2].u32</b>: day of the selected date.</li> </ul>

**Since**: 12


