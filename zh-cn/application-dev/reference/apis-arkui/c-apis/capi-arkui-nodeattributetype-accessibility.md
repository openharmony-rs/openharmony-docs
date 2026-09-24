# 无障碍

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_ACCESSIBILITY_GROUP

```c
NODE_ACCESSIBILITY_GROUP
```

**描述：**

无障碍组属性，支持属性设置、属性重置和属性获取。 作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32: 为1时表示该组件及其所有子组件合并为一个可被无障碍服务整体聚焦的组件，无障碍服务将不再单独关注其子组件内容；为0时表示各子组件可被无障碍服务单独聚焦。 参数取值为1或0，传入非法值时该设置不生效。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32: 为1时表示该组件及其所有子组件合并为一个可被无障碍服务整体聚焦的组件，无障碍服务将不再单独关注其子组件内容；为0时表示各子组件可被无障碍服务单独聚焦。返回值取值为1或0。</li> </ul>

**起始版本：** 12

### NODE_ACCESSIBILITY_TEXT

```c
NODE_ACCESSIBILITY_TEXT
```

**描述：**

无障碍文本属性，支持属性设置、属性重置和属性获取。 作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string: 无障碍文本，无长度限制。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string: 组件的无障碍文本内容，用于在无障碍服务中朗读或展示该组件的文本描述。</li> </ul>

**起始版本：** 12

### NODE_ACCESSIBILITY_MODE

```c
NODE_ACCESSIBILITY_MODE
```

**描述：**

无障碍辅助服务模式，支持属性设置、属性重置和属性获取。 作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32: 辅助服务模式，参数类型为ArkUI_AccessibilityMode。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32: 辅助服务模式，返回值类型为ArkUI_AccessibilityMode。</li> </ul>

**起始版本：** 12

### NODE_ACCESSIBILITY_DESCRIPTION

```c
NODE_ACCESSIBILITY_DESCRIPTION
```

**描述：**

无障碍说明属性，支持属性设置、属性重置和属性获取。 作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string: 无障碍说明，无长度限制。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string: 组件的无障碍说明内容，用于向无障碍服务补充描述该组件的详细用途或操作指引。</li> </ul>

**起始版本：** 12

### NODE_ACCESSIBILITY_ID

```c
NODE_ACCESSIBILITY_ID = 87
```

**描述：**

无障碍自定义标识ID，支持属性获取。 作为属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32: 无障碍自定义标识ID。</li> </ul>

**起始版本：** 12

### NODE_ACCESSIBILITY_ACTIONS

```c
NODE_ACCESSIBILITY_ACTIONS = 88
```

**描述：**

无障碍操作类型属性，支持属性设置、属性重置和属性获取。 作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32: 配置无障碍操作类型，参数类型ArkUI_AccessibilityActionType。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32: 无障碍操作类型，返回值类型为ArkUI_AccessibilityActionType。</li> </ul>

**起始版本：** 12

### NODE_ACCESSIBILITY_ROLE

```c
NODE_ACCESSIBILITY_ROLE = 89
```

**描述：**

定义无障碍角色属性，支持属性设置、属性重置和属性获取。 作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32: 无障碍角色，参数类型ArkUI_NodeType。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32: 无障碍角色，返回值类型为ArkUI_NodeType。</li> </ul>

**起始版本：** 12

### NODE_ACCESSIBILITY_STATE

```c
NODE_ACCESSIBILITY_STATE = 90
```

**描述：**

定义无障碍状态属性，支持属性设置、属性重置和属性获取。 作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: 无障碍状态信息，参数类型[ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: 返回值类型为[ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md)。</li> </ul>

**起始版本：** 12

### NODE_ACCESSIBILITY_VALUE

```c
NODE_ACCESSIBILITY_VALUE = 91
```

**描述：**

定义无障碍值属性，支持属性设置、属性重置和属性获取。 作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: 无障碍值信息，参数类型为[ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: 返回值类型为[ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md)。</li> </ul>

**起始版本：** 12

### NODE_ACCESSIBILITY_NEXT_FOCUS_ID

```c
NODE_ACCESSIBILITY_NEXT_FOCUS_ID = 124
```

**描述：**

无障碍下一焦点ID属性，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string: 无障碍下一焦点ID。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string: 无障碍下一焦点ID。</li> </ul>

**起始版本：** 26.0.0

### NODE_ACCESSIBILITY_DEFAULT_FOCUS

```c
NODE_ACCESSIBILITY_DEFAULT_FOCUS = 125
```

**描述：**

设置无障碍默认焦点标志，用于无障碍服务查找默认焦点组件。支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32: 无障碍默认焦点。为<b>1</b>时表示该组件在无障碍服务中被定义为默认焦点。</li> <li>参数取值为<b>1</b>或<b>0</b>。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32: 无障碍默认焦点。为<b>1</b>时表示该组件在无障碍服务中被定义为默认焦点。</li> <li>参数取值为<b>1</b>或<b>0</b>。</li> </ul>

**起始版本：** 26.0.0


