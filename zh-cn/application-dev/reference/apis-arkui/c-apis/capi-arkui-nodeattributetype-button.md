# 按钮

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_BUTTON_LABEL

```c
NODE_BUTTON_LABEL = MAX_NODE_SCOPE_NUM * ARKUI_NODE_BUTTON
```

**描述：**

Defines the button text content. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.string: default text content.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.string: default text content.</li> </ul>

**起始版本：** 12

### NODE_BUTTON_TYPE

```c
NODE_BUTTON_TYPE
```

**描述：**

Sets the button type. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].i32: button type. The parameter type is [ArkUI_ButtonType](capi-button-h.md#arkui_buttontype). The default value is <b>ARKUI_BUTTON_TYPE_CAPSULE</b>.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].i32: button type. The parameter type is [ArkUI_ButtonType](capi-button-h.md#arkui_buttontype). The default value is <b>ARKUI_BUTTON_TYPE_CAPSULE</b>.</li> </ul>

**起始版本：** 12

### NODE_BUTTON_MIN_FONT_SCALE

```c
NODE_BUTTON_MIN_FONT_SCALE
```

**描述：**

Defines the minimum font scale attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: minimum font scale, in fp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: minimum font scale, in fp.</li> </ul>

**起始版本：** 18

### NODE_BUTTON_MAX_FONT_SCALE

```c
NODE_BUTTON_MAX_FONT_SCALE
```

**描述：**

Defines the maximum font scale attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:** <ul> <li>.value[0].f32: maximum font scale, in fp.</li> </ul> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):** <ul> <li>.value[0].f32: maximum font scale, in fp.</li> </ul>

**起始版本：** 18


