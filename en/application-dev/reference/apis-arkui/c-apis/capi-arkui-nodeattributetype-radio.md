# Radio

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

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

Style of the radio button in selected or deselected state. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0]?.u32: Color of the background when the radio button is selected, in 0xARGB format. The default value is **0xFF007DFF**.</li> <li>.value[1]?.u32: Color of the border when the radio button is deselected, in 0xARGB format. The default value is **0xFF182431**.</li> <li>.value[2]?.u32: Color of the indicator when the radio button is selected, in 0xARGB format. The default value is **0xFFFFFFFF**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: Color of the background when the radio button is selected, in 0xARGB format. The default value is **0xFF007DFF**.</li> <li>.value[1].u32: Color of the border when the radio button is deselected, in 0xARGB format. The default value is **0xFF182431**.</li> <li>.value[2].u32: Color of the indicator when the radio button is selected, in 0xARGB format. The default value is **0xFFFFFFFF**.</li> </ul>

**Since**: 12

### NODE_RADIO_VALUE

```c
NODE_RADIO_VALUE
```

**Description**

Current value of the radio button. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.string: Current value of the radio button.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.string: Current value of the radio button.</li> </ul>

**Since**: 12

### NODE_RADIO_GROUP

```c
NODE_RADIO_GROUP
```

**Description**

Name of the group to which the radio button belongs. Only one radio button in a given group can be selected at a time. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.string: Name of the group to which the radio button belongs.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.string: Name of the group to which the radio button belongs.</li> </ul>

**Since**: 12


