# 同应用进程嵌入式组件

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_EMBEDDED_COMPONENT_WANT

```c
NODE_EMBEDDED_COMPONENT_WANT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_EMBEDDED_COMPONENT
```

**描述：**

定义用于启动EmbeddedUIExtensionAbility的want参数。 支持属性设置。使用场景：当应用需要在当前页面嵌入EmbeddedUIExtensionAbility（同应用或满足跨应用嵌入权限条件的EmbeddedUIExtensionAbility）时， 通过该属性指定目标EmbeddedUIExtensionAbility。 作为属性设置方法参数时，[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: EmbeddedComponent的want参数，用于指定启动EmbeddedUIExtensionAbility所需的目标信息。参数类型为[AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md)。 默认值为nullptr。</li> </ul>

**起始版本：** 20

### NODE_EMBEDDED_COMPONENT_OPTION

```c
NODE_EMBEDDED_COMPONENT_OPTION
```

**描述：**

定义EmbeddedComponent的运行选项，用于设置EmbeddedComponent组件的运行异常回调（onError）和正常退出回调（onTerminated）。 支持属性设置。 作为属性设置方法参数时，[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object: EmbeddedComponent的运行选项。参数类型为[ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)。默认值为nullptr。</li> </ul>

**起始版本：** 20


