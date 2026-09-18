# Slider

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_SLIDER_EVENT_ON_CHANGE

```c
NODE_SLIDER_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SLIDER
```

**Description**

Defines the event triggered when the <b>ARKUI_NODE_SLIDER</b> component is dragged or clicked.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br><ul><br><li><b>ArkUI_NodeComponentEvent.data[0].f32</b>: current slider value.</li> <br><li><b>ArkUI_NodeComponentEvent.data[1].i32</b>: state triggered by the event.</li> </ul>

**Since**: 12


