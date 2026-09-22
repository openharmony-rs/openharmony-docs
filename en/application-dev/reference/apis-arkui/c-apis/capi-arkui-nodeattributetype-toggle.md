# Toggle

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TOGGLE_SELECTED_COLOR

```c
NODE_TOGGLE_SELECTED_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TOGGLE
```

**Description**

Defines the color of the component when it is selected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: background color, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TOGGLE_SWITCH_POINT_COLOR

```c
NODE_TOGGLE_SWITCH_POINT_COLOR
```

**Description**

Defines the color of the circular slider for the component of the switch type. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: color of the circular slider, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: color of the circular slider, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TOGGLE_VALUE

```c
NODE_TOGGLE_VALUE
```

**Description**

Defines the toggle switch value. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: whether to enable the toggle. The value <b>true</b> means to enable the toggle.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: whether to enable the toggle.</li> </ul>

**Since**: 12

### NODE_TOGGLE_UNSELECTED_COLOR

```c
NODE_TOGGLE_UNSELECTED_COLOR
```

**Description**

Defines the color of the component when it is deselected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: background color, in 0xARGB format.</li> </ul>

**Since**: 12


