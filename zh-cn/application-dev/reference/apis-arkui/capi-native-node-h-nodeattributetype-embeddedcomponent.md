# ArkUI_NodeAttributeType（EmbeddedComponent组件相关属性）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## 概述

定义ArkUI在Native侧可以设置的EmbeddedComponent组件相关属性样式集合，支持配置启动EmbeddedUIExtensionAbility的want参数以及设置EmbeddedComponent组件的运行异常回调（onError）和正常退出回调（onTerminated）等运行选项，适用于需要在Native侧对嵌入式组件进行属性设置的场景。EmbeddedComponent适用于需要在当前应用页面内嵌入本应用（或满足跨应用嵌入权限条件的）EmbeddedUIExtensionAbility提供的UI页面的场景。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

## NODE_EMBEDDED_COMPONENT_WANT

```c
NODE_EMBEDDED_COMPONENT_WANT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_EMBEDDED_COMPONENT = 1016000
```

定义用于启动EmbeddedUIExtensionAbility的want参数。支持属性设置。使用场景：当应用需要在当前页面嵌入EmbeddedUIExtensionAbility（同应用或满足跨应用嵌入权限条件的EmbeddedUIExtensionAbility）时，通过该属性指定目标EmbeddedUIExtensionAbility。<br>
作为属性设置方法参数时，[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | EmbeddedComponent的want参数，用于指定启动EmbeddedUIExtensionAbility所需的目标信息。参数类型为[AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md)。默认值为nullptr。 |

## NODE_EMBEDDED_COMPONENT_OPTION

```c
NODE_EMBEDDED_COMPONENT_OPTION = 1016001
```

定义EmbeddedComponent的运行选项，用于设置EmbeddedComponent组件的运行异常回调（onError）和正常退出回调（onTerminated）。支持属性设置。<br>
作为属性设置方法参数时，[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | EmbeddedComponent的运行选项。参数类型为[ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)。默认值为nullptr。 |
