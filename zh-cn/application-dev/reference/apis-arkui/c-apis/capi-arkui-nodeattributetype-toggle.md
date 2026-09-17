# 切换按钮

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_TOGGLE_SELECTED_COLOR

```c
NODE_TOGGLE_SELECTED_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TOGGLE
```

**描述：**

Defines the color of the component when it is selected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].u32: background color, in 0xARGB format.</li> </ul>

**起始版本：** 12

### NODE_TOGGLE_SWITCH_POINT_COLOR

```c
NODE_TOGGLE_SWITCH_POINT_COLOR
```

**描述：**

Defines the color of the circular slider for the component of the switch type. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: color of the circular slider, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].u32: color of the circular slider, in 0xARGB format.</li> </ul>

**起始版本：** 12

### NODE_TOGGLE_VALUE

```c
NODE_TOGGLE_VALUE
```

**描述：**

Defines the toggle switch value. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to enable the toggle. The value <b>true</b> means to enable the toggle.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].i32: whether to enable the toggle.</li> </ul>

**起始版本：** 12

### NODE_TOGGLE_UNSELECTED_COLOR

```c
NODE_TOGGLE_UNSELECTED_COLOR
```

**描述：**

Defines the color of the component when it is deselected. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> <br></ul><br><br>**Format of the return value {@link ArkUI_AttributeItem}:** <ul> <li>.value[0].u32: background color, in 0xARGB format.</li> </ul>

**起始版本：** 12


