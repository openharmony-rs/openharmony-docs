# Datepicker

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_DATE_PICKER_EVENT_ON_DATE_CHANGE

```c
NODE_DATE_PICKER_EVENT_ON_DATE_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER
```

**Description**

Defines the event triggered when a date is selected in the <b>ARKUI_NODE_DATE_PICKER</b> component.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains three parameters:<br><ul><br><li><b>ArkUI_NodeComponentEvent.data[0].i32</b>: year of the selected date.</li><br><li><b>ArkUI_NodeComponentEvent.data[1].i32</b>: month of the selected date. Value range: [0-11].</li><br><li><b>ArkUI_NodeComponentEvent.data[2].i32</b>: day of the selected date.</li> </ul>

**Since**: 12


