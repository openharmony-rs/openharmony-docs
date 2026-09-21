# 复选框群组

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_CHECKBOX_GROUP_NAME

```c
NODE_CHECKBOX_GROUP_NAME  = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP
```

**描述：**

Defines the name of the checkboxgroup. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.string: component name.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.string: component name.</li> </ul>

**起始版本：** 15

### NODE_CHECKBOX_GROUP_SELECT_ALL

```c
NODE_CHECKBOX_GROUP_SELECT_ALL
```

**描述：**

Defines whether the checkboxgroup is selected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: whether the checkboxgroup is selected. The value <b>1</b> means that the checkboxgroup is selected, and <b>0</b> means the opposite.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: The value <b>1</b> means that the checkboxgroup is selected, and <b>0</b> means the opposite.</li> </ul>

**起始版本：** 15

### NODE_CHECKBOX_GROUP_SELECTED_COLOR

```c
NODE_CHECKBOX_GROUP_SELECTED_COLOR
```

**描述：**

Defines the color of the checkboxgroup when it is selected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: color of the checkboxgroup when it is selected, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: color of the checkboxgroup when it is selected, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul>

**起始版本：** 15

### NODE_CHECKBOX_GROUP_UNSELECTED_COLOR

```c
NODE_CHECKBOX_GROUP_UNSELECTED_COLOR
```

**描述：**

Defines the border color of the checkboxgroup when it is not selected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> </ul>

**起始版本：** 15

### NODE_CHECKBOX_GROUP_MARK

```c
NODE_CHECKBOX_GROUP_MARK
```

**描述：**

Defines the internal icon style of the checkboxgroup. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> <li>.value[1]?.f32: size of the internal mark, in vp. Optional.</li> <li>.value[2]?.f32: stroke width of the internal mark, in vp. Optional. The default value is <b>2</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].u32: border color, in 0xARGB format, for example, <b>0xFF1122FF</b>.</li> <li>.value[1].f32: size of the internal mark, in vp.</li> <li>.value[2].f32: stroke width of the internal mark, in vp. The default value is <b>2</b>.</li> </ul>

**起始版本：** 15

### NODE_CHECKBOX_GROUP_SHAPE

```c
NODE_CHECKBOX_GROUP_SHAPE
```

**描述：**

Defines the shape of the checkboxgroup. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: component shape. The parameter type is [ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape).</li> </ul>

**起始版本：** 15


