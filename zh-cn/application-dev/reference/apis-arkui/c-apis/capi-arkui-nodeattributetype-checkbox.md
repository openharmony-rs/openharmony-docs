# 复选框

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_CHECKBOX_SELECT

```c
NODE_CHECKBOX_SELECT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX
```

**描述：**

CheckBox多选框是否选中，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 1表示选中，0表示不选中。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 1表示选中，0表示不选中。</li> </ul>

**起始版本：** 12

### NODE_CHECKBOX_SELECT_COLOR

```c
NODE_CHECKBOX_SELECT_COLOR
```

**描述：**

CheckBox多选框选中状态颜色，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 多选框选中状态颜色，类型为0xARGB，如0xFF1122FF。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 多选框选中状态颜色，类型为0xARGB，如0xFF1122FF。</li> </ul>

**起始版本：** 12

### NODE_CHECKBOX_UNSELECT_COLOR

```c
NODE_CHECKBOX_UNSELECT_COLOR
```

**描述：**

CheckBox多选框非选中状态边框颜色，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 边框颜色，类型为0xARGB，如0xFF1122FF。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 边框颜色，类型为0xARGB，如0xFF1122FF。</li> </ul>

**起始版本：** 12

### NODE_CHECKBOX_MARK

```c
NODE_CHECKBOX_MARK
```

**描述：**

CheckBox多选框内部图标样式，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 边框颜色，类型为0xARGB，如0xFF1122FF。</li> <li>.value[1]?.f32: 可选，内部图标大小，单位vp。</li> <li>.value[2]?.f32: 可选，内部图标粗细，单位vp，默认值2。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 边框颜色，类型为0xARGB，如0xFF1122FF。</li> <li>.value[1].f32: 内部图标大小，单位vp。</li> <li>.value[2].f32: 内部图标粗细，单位vp，默认值2。</li> </ul>

**起始版本：** 12

### NODE_CHECKBOX_SHAPE

```c
NODE_CHECKBOX_SHAPE
```

**描述：**

CheckBox组件形状，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 组件形状，参数类型[ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape)。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 组件形状，参数类型[ArkUI_CheckboxShape](capi-checkbox-h.md#arkui_checkboxshape)。</li> </ul>

**起始版本：** 12

### NODE_CHECKBOX_NAME

```c
NODE_CHECKBOX_NAME
```

**描述：**

定义复选框的名称，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.string: 组件名称。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.string: 组件名称。</li> </ul>

**起始版本：** 15

### NODE_CHECKBOX_GROUP

```c
NODE_CHECKBOX_GROUP
```

**描述：**

定义复选框的组的名称，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.string: 组名称。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.string: 组名称。</li> </ul>

**起始版本：** 15


