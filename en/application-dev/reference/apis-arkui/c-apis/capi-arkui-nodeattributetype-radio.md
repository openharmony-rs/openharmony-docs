# Radio

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_RADIO_CHECKED

```c
NODE_RADIO_CHECKED = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RADIO
```

**Description**

Set the selection status of an option button. Attribute setting, attribute resetting, and attribute obtaining are supported. **Attribute setting method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) Parameter format:** <ul> <li>.value[0].i32: check status of an option button. The default value is false.</li> </ul> **Attribute obtaining method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:** <ul> <li>.value[0].i32: selection status of an option button.</li> </ul>

**Since**: 12

### NODE_RADIO_STYLE

```c
NODE_RADIO_STYLE
```

**Description**

Set the styles of the selected and deselected states of the option button. The attribute setting, attribute resetting, and attribute obtaining are supported. **Attribute setting method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) Parameter format:** <ul> <li>.value[0]?. u32: color of the mother board in enabled state. The type is 0xARGB, and the default value is 0xFF007DFF.</li> <li>.value[1]?. u32: stroke color in the close state. The type is 0xARGB, and the default value is 0xFF182431.</li> <li>.value[2]?. u32: color of the internal round pie in the enabled state. The type is 0xARGB, and the default value is 0xFFFFFFFF.</li> </ul> **Attribute obtaining method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:** <ul> <li>.value[0]. u32: color of the mother board in enabled state. The type is 0xARGB, and the default value is 0xFF007DFF.</li> <li>.value[1]. u32: stroke color in the close state. The type is 0xARGB, and the default value is 0xFF182431.</li> <li>.value[2]. u32: color of the internal round pie in the enabled state. The type is 0xARGB, and the default value is 0xFFFFFFF.</li> </ul>

**Since**: 12

### NODE_RADIO_VALUE

```c
NODE_RADIO_VALUE
```

**Description**

Sets the value of the current radio. This attribute can be set, reset, and obtained as required through APIs.<br> **Attribute setting method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) Parameter format:** <ul> <li>.string: radio value.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.string: radio value.</li> </ul>

**Since**: 12

### NODE_RADIO_GROUP

```c
NODE_RADIO_GROUP
```

**Description**

Set the group name of the current Radio group, only one radio of the same group can be selected. This attribute can be set, reset, and obtained as required through APIs.<br> **Attribute setting method [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) Parameter format:** <ul> <li>.string: name of the group to which the current option box belongs.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.string: name of the group to which the current option box belongs.</li> </ul>

**Since**: 12


