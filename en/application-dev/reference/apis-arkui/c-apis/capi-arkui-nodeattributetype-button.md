# Button

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_BUTTON_LABEL

```c
NODE_BUTTON_LABEL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_BUTTON
```

**Description**

Defines the button text content. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.string: default text content.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.string: default text content.</li> </ul>

**Since**: 12

### NODE_BUTTON_TYPE

```c
NODE_BUTTON_TYPE
```

**Description**

Sets the button type. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: button type. The parameter type is [ArkUI_ButtonType](capi-button-h.md#arkui_buttontype). The default value is <b>ARKUI_BUTTON_TYPE_CAPSULE</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: button type. The parameter type is [ArkUI_ButtonType](capi-button-h.md#arkui_buttontype). The default value is <b>ARKUI_BUTTON_TYPE_CAPSULE</b>.</li> </ul>

**Since**: 12

### NODE_BUTTON_MIN_FONT_SCALE

```c
NODE_BUTTON_MIN_FONT_SCALE
```

**Description**

Defines the minimum font scale attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: minimum font scale, in fp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: minimum font scale, in fp.</li> </ul>

**Since**: 18

### NODE_BUTTON_MAX_FONT_SCALE

```c
NODE_BUTTON_MAX_FONT_SCALE
```

**Description**

Defines the maximum font scale attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: maximum font scale, in fp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: maximum font scale, in fp.</li> </ul>

**Since**: 18


