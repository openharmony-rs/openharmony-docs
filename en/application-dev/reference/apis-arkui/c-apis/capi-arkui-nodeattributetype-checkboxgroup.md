# CheckboxGroup

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_CHECKBOX_GROUP_NAME

```c
NODE_CHECKBOX_GROUP_NAME  = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP
```

**Description**

Defines the name of the checkboxgroup. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.string: component name.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.string: component name.</li> </ul>

**Since**: 15

### NODE_CHECKBOX_GROUP_SELECT_ALL

```c
NODE_CHECKBOX_GROUP_SELECT_ALL
```

**Description**

Whether to select all check boxes in the **CheckBoxGroup** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: Whether to select all check boxes in the **CheckBoxGroup** component. The value **1** means to select all check boxes, and **0** means the opposite.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: Whether all check boxes are selected. The value **1** means that all check boxes are selected, and **0** means the opposite.</li> </ul>

**Since**: 15

### NODE_CHECKBOX_GROUP_SELECTED_COLOR

```c
NODE_CHECKBOX_GROUP_SELECTED_COLOR
```

**Description**

Color for the selected state of the **CheckBoxGroup** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: Color of the selected state, in 0xARGB format, for example, **0xFF1122FF**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: Color for the selected state of the **CheckBoxGroup** component, in 0xARGB format, for example, **0xFF1122FF**.</li> </ul>

**Since**: 15

### NODE_CHECKBOX_GROUP_UNSELECTED_COLOR

```c
NODE_CHECKBOX_GROUP_UNSELECTED_COLOR
```

**Description**

Border color for the unselected state of the **CheckBoxGroup** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: Border color, in 0xARGB format, for example, **0xFF1122FF**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: Border color, in 0xARGB format, for example, **0xFF1122FF**.</li> </ul>

**Since**: 15

### NODE_CHECKBOX_GROUP_MARK

```c
NODE_CHECKBOX_GROUP_MARK
```

**Description**

Internal mark style of the **CheckBoxGroup** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: Border color, in 0xARGB format, for example, **0xFF1122FF**.</li> <li>.value[1]?.f32: Size of the internal mark, in vp. This parameter is optional.</li> <li>.value[2]?.f32: Stroke width of the internal mark, in vp. This parameter is optional. The default value is **2**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: Border color, in 0xARGB format, for example, **0xFF1122FF**.</li> <li>.value[1]?.f32: Size of the internal mark, in vp. This parameter is optional.</li> <li>.value[2]?.f32: Stroke width of the internal mark, in vp. This parameter is optional. The default value is **2**.</li> </ul>

**Since**: 15

### NODE_CHECKBOX_GROUP_SHAPE

```c
NODE_CHECKBOX_GROUP_SHAPE
```

**Description**

Shape of the **CheckBoxGroup** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: Component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: Component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).</li> </ul>

**Since**: 15


