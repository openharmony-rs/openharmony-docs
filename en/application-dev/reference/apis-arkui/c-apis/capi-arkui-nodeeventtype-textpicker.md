# Textpicker

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TEXT_PICKER_EVENT_ON_CHANGE

```c
NODE_TEXT_PICKER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER
```

**Description**

Defines the event triggered when an item is selected in the <b>ARKUI_NODE_TEXT_PICKER</b> component.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br><ul><br><li><b>ArkUI_NodeComponentEvent.data[0...11].i32</b>: value of the selected item.</li> </ul>

**Since**: 12

### NODE_TEXT_PICKER_EVENT_ON_SCROLL_STOP

```c
NODE_TEXT_PICKER_EVENT_ON_SCROLL_STOP = 15001
```

**Description**

Defines the event triggered when an item is selected and scrolling has stopped in the <b>ARKUI_NODE_TEXT_PICKER</b> component.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:<br><ul><br><li><b>ArkUI_NodeComponentEvent.data[0...11].i32</b>: value of the selected item.</li> </ul>

**Since**: 14


