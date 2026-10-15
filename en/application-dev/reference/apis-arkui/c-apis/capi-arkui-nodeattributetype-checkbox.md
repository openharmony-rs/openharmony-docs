# Checkbox

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_CHECKBOX_SELECT

```c
NODE_CHECKBOX_SELECT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX
```

**Description**

Defines whether the check box is selected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: whether the check box is selected. The value <b>1</b> means that the check box is selected, and <b>0</b> means the opposite.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: The value <b>1</b> means that the check box is selected, and <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_CHECKBOX_SELECT_COLOR

```c
NODE_CHECKBOX_SELECT_COLOR
```

**Description**

Color of the **CheckBox** component when it is selected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: Color of the check box when it is selected, in 0xARGB format, for example, **0xFF1122FF**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: Color of the check box when it is selected, in 0xARGB format, for example, **0xFF1122FF**.</li> </ul>

**Since**: 12

### NODE_CHECKBOX_UNSELECT_COLOR

```c
NODE_CHECKBOX_UNSELECT_COLOR
```

**Description**

Border color of the **CheckBox** component when it is not selected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: Border color, in 0xARGB format, for example, **0xFF1122FF**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: Border color, in 0xARGB format, for example, **0xFF1122FF**.</li> </ul>

**Since**: 12

### NODE_CHECKBOX_MARK

```c
NODE_CHECKBOX_MARK
```

**Description**

Internal mark style of the **CheckBox** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: Border color, in 0xARGB format, for example, **0xFF1122FF**.</li> <li>.value[1]?.f32: Size of the internal mark, in vp. This parameter is optional.</li> <li>.value[2]?.f32: Stroke width of the internal mark, in vp. This parameter is optional. The default value is **2**.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: Border color, in 0xARGB format, for example, **0xFF1122FF**.</li> <li>.value[1].f32: Size of the internal mark, in vp.</li> <li>.value[2].f32: Stroke width of the internal mark, in vp. The default value is **2**.</li> </ul>

**Since**: 12

### NODE_CHECKBOX_SHAPE

```c
NODE_CHECKBOX_SHAPE
```

**Description**

Shape of the **CheckBox** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: Component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: Component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).</li> </ul>

**Since**: 12

### NODE_CHECKBOX_NAME

```c
NODE_CHECKBOX_NAME
```

**Description**

Name of the **CheckBox** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.string: Component name.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.string: Component name.</li> </ul>

**Since**: 15

### NODE_CHECKBOX_GROUP

```c
NODE_CHECKBOX_GROUP
```

**Description**

Name of the **CheckboxGroup** component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.string: Component name.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.string: Component name.</li> </ul>

**Since**: 15


