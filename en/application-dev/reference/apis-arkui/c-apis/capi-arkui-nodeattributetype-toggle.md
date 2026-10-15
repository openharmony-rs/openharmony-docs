# Toggle

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

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

Color of the circular thumb for the component of the switch type. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: Color of the circular thumb, in 0xARGB format. For example, **0xFFFF0000** indicates red.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: Color of the circular thumb, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TOGGLE_VALUE

```c
NODE_TOGGLE_VALUE
```

**Description**

Toggle value of the component of the switch type. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: Whether to enable the toggle. The value **true** means to enable the toggle.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: Whether the toggle is enabled.</li> </ul>

**Since**: 12

### NODE_TOGGLE_UNSELECTED_COLOR

```c
NODE_TOGGLE_UNSELECTED_COLOR
```

**Description**

Color of the component when it is deselected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: Background color, in 0xARGB format. For example, **0xFFFF0000** indicates red.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: Background color, in 0xARGB format.</li> </ul>

**Since**: 12


