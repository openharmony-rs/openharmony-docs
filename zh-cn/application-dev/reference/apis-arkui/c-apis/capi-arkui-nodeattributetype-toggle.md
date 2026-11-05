# 切换按钮

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_TOGGLE_SELECTED_COLOR

```c
NODE_TOGGLE_SELECTED_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TOGGLE
```

**描述：**

组件打开状态的背景颜色属性。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 背景色数值，0xARGB格式，形如 0xFFFF0000 表示红色。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 背景色数值，0xARGB格式。</li> </ul>

**起始版本：** 12

### NODE_TOGGLE_SWITCH_POINT_COLOR

```c
NODE_TOGGLE_SWITCH_POINT_COLOR
```

**描述：**

Switch类型的圆形滑块颜色属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 圆形滑块颜色数值，0xARGB格式，形如 0xFFFF0000 表示红色。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 圆形滑块颜色数值，0xARGB格式。</li> </ul>

**起始版本：** 12

### NODE_TOGGLE_VALUE

```c
NODE_TOGGLE_VALUE
```

**描述：**

Switch类型的开关值，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 设置开关的值，true表示开启。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 设置开关的值。</li> </ul>

**起始版本：** 12

### NODE_TOGGLE_UNSELECTED_COLOR

```c
NODE_TOGGLE_UNSELECTED_COLOR
```

**描述：**

组件关闭状态的背景颜色属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 背景色数值，0xARGB格式，形如 0xFFFF0000 表示红色。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].u32: 背景色数值，0xARGB格式。</li> </ul>

**起始版本：** 12


