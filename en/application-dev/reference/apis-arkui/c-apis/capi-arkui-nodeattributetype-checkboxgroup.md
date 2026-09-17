# CheckboxGroup

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_CHECKBOX_GROUP_NAME

```c
NODE_CHECKBOX_GROUP_NAME  = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP
```

**Description**

Defines the name of the checkboxgroup. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: component name.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.string: component name.</li> </ul>

**Since**: 15

### NODE_CHECKBOX_GROUP_SELECT_ALL

```c
NODE_CHECKBOX_GROUP_SELECT_ALL
```

**Description**

Defines whether the checkboxgroup is selected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether the checkboxgroup is selected.<br>The value <b>1</b> means that the checkboxgroup is selected, and <b>0</b> means the opposite.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].i32: The value <b>1</b> means that the checkboxgroup is selected, and <b>0</b> means the opposite.</li> </ul>

**Since**: 15

### NODE_CHECKBOX_GROUP_SELECTED_COLOR

```c
NODE_CHECKBOX_GROUP_SELECTED_COLOR
```

**Description**

Defines the color of the checkboxgroup when it is selected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: color of the checkboxgroup when it is selected, in 0xARGB format,<br>for example, <b>0xFF1122FF</b>.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].u32: color of the checkboxgroup when it is selected, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul>

**Since**: 15

### NODE_CHECKBOX_GROUP_UNSELECTED_COLOR

```c
NODE_CHECKBOX_GROUP_UNSELECTED_COLOR
```

**Description**

Defines the border color of the checkboxgroup when it is not selected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul>

**Since**: 15

### NODE_CHECKBOX_GROUP_MARK

```c
NODE_CHECKBOX_GROUP_MARK
```

**Description**

Defines the internal icon style of the checkboxgroup. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li><br><li>.value[1]?.f32: size of the internal mark, in vp. Optional.</li><br><li>.value[2]?.f32: stroke width of the internal mark, in vp. Optional. The default value is <b>2</b>.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li><br><li>.value[1].f32: size of the internal mark, in vp.</li> <br><li>.value[2].f32: stroke width of the internal mark, in vp. The default value is <b>2</b>.</li> </ul>

**Since**: 15

### NODE_CHECKBOX_GROUP_SHAPE

```c
NODE_CHECKBOX_GROUP_SHAPE
```

**Description**

Defines the shape of the checkboxgroup. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: component shape. The parameter type is {@link ArkUI_CheckboxShape}.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: component shape. The parameter type is {@link ArkUI_CheckboxShape}.</li> </ul>

**Since**: 15


