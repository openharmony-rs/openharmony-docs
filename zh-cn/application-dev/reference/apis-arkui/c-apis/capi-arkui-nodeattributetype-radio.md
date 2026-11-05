# 单选框

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_RADIO_CHECKED

```c
NODE_RADIO_CHECKED = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RADIO
```

**描述：**

设置单选框的选中状态，支持属性设置，属性重置和属性获取。 **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 单选框的选中状态，默认值false。值为true时，单选框被选中。值为false时，单选框不被选中。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0].i32: 单选框的选中状态。</li> </ul>

**起始版本：** 12

### NODE_RADIO_STYLE

```c
NODE_RADIO_STYLE
```

**描述：**

设置单选框选中状态和非选中状态的样式，支持属性设置，属性重置和属性获取。 **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0]?. u32: 开启状态底板颜色，类型为0xARGB，默认值为0xFF007DFF。</li> <li>.value[1]?. u32: 关闭状态描边颜色，类型为0xARGB，默认值为0xFF182431。</li> <li>.value[2]?. u32: 开启状态内部圆饼颜色，类型为0xARGB，默认值为0xFFFFFFFF。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.value[0]. u32: 开启状态底板颜色，类型为0xARGB，默认值为0xFF007DFF。</li> <li>.value[1]. u32: 关闭状态描边颜色，类型为0xARGB，默认值为0xFF182431。</li> <li>.value[2]. u32: 开启状态内部圆饼颜色，类型为0xARGB，默认值为0xFFFFFFFF。</li> </ul>

**起始版本：** 12

### NODE_RADIO_VALUE

```c
NODE_RADIO_VALUE
```

**描述：**

设置当前单选框的值，支持属性设置、重置和获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.string: 单选框的值。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.string: 单选框的值。</li> </ul>

**起始版本：** 12

### NODE_RADIO_GROUP

```c
NODE_RADIO_GROUP
```

**描述：**

设置当前单选框的所属群组名称，相同group的Radio只能有一个被选中，支持属性设置、重置和获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.string: 当前单选框的所属群组名称。</li> </ul> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：** <ul> <li>.string: 当前单选框的所属群组名称。</li> </ul>

**起始版本：** 12


