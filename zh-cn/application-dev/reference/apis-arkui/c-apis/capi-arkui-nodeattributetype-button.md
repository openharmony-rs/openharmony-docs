# 按钮

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_BUTTON_LABEL

```c
NODE_BUTTON_LABEL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_BUTTON
```

**描述：**

Button按钮的文本内容属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.string: 默认文本的内容。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.string: 默认文本的内容。</li> </ul>

**起始版本：** 12

### NODE_BUTTON_TYPE

```c
NODE_BUTTON_TYPE
```

**描述：**

Button按钮的类型属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 设置Button按钮的类型，参数类型[ArkUI_ButtonType](capi-button-h.md#arkui_buttontype)，默认值为ARKUI_BUTTON_TYPE_CAPSULE。 </li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 获取Button按钮的类型，参数类型[ArkUI_ButtonType](capi-button-h.md#arkui_buttontype)，默认值为ARKUI_BUTTON_TYPE_CAPSULE。 </li> </ul>

**起始版本：** 12

### NODE_BUTTON_MIN_FONT_SCALE

```c
NODE_BUTTON_MIN_FONT_SCALE
```

**描述：**

Button按钮的最小字体缩放倍数属性，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 设置Button按钮的最小字体缩放倍数，默认单位fp。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 获取Button按钮的最小字体缩放倍数，默认单位fp。</li> </ul>

**起始版本：** 18

### NODE_BUTTON_MAX_FONT_SCALE

```c
NODE_BUTTON_MAX_FONT_SCALE
```

**描述：**

Button按钮的最大字体缩放倍数属性，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 设置Button按钮的最大字体缩放倍数，默认单位fp。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].f32: 获取Button按钮的最大字体缩放倍数，默认单位fp。</li> </ul>

**起始版本：** 18


