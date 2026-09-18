# 单选框

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_RADIO_CHECKED

```c
NODE_RADIO_CHECKED = MAX_NODE_SCOPE_NUM * ARKUI_NODE_RADIO
```

**描述：**

Set the selection status of an option button. Attribute setting, attribute resetting, and attribute obtaining are supported. **Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:**<br><ul><br><li>.value[0].i32: check status of an option button. The default value is false.</li><br></ul><br>**Attribute obtaining method return value {@Link ArkUI_AttributeItem} format:** <ul> <li>.value[0].i32: selection status of an option button.</li> </ul>

**起始版本：** 12

### NODE_RADIO_STYLE

```c
NODE_RADIO_STYLE
```

**描述：**

Set the styles of the selected and deselected states of the option button. The attribute setting, attribute resetting, and attribute obtaining are supported. **Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:**<br><ul><br><li>.value[0]?. u32: color of the mother board in enabled state. <br>The type is 0xARGB, and the default value is 0xFF007DFF.</li> <br><li>.value[1]?. u32: stroke color in the close state. The type is 0xARGB, <br>and the default value is 0xFF182431.</li> <br><li>.value[2]?. u32: color of the internal round pie in the enabled state. <br>The type is 0xARGB, and the default value is 0xFFFFFFFF.</li> <br></ul><br>**Attribute obtaining method return value {@Link ArkUI_AttributeItem} format:** <ul> <li>.value[0]. u32: color of the mother board in enabled state. <br>The type is 0xARGB, and the default value is 0xFF007DFF.</li> <br><li>.value[1]. u32: stroke color in the close state. The type is 0xARGB, <br>and the default value is 0xFF182431.</li> <br><li>.value[2]. u32: color of the internal round pie in the enabled state. The type is 0xARGB, and the default value is 0xFFFFFFF.</li> </ul>

**起始版本：** 12

### NODE_RADIO_VALUE

```c
NODE_RADIO_VALUE
```

**描述：**

Sets the value of the current radio. This attribute can be set, reset, and obtained as required through APIs.<br> **Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:**<br><ul><br><li>.string: radio value.</li><br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.string: radio value.</li> </ul>

**起始版本：** 12

### NODE_RADIO_GROUP

```c
NODE_RADIO_GROUP
```

**描述：**

Set the group name of the current Radio group, only one radio of the same group can be selected. This attribute can be set, reset, and obtained as required through APIs.<br> **Attribute setting method {@Link ArkUI_AttributeItem} Parameter format:**<br><ul><br><li>.string: name of the group to which the current option box belongs.</li><br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.string: name of the group to which the current option box belongs.</li> </ul>

**起始版本：** 12


