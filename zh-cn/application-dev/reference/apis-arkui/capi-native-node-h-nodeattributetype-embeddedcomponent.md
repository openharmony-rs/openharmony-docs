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

定义ArkUI在Native侧可以设置的EmbeddedComponent组件相关属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

## NODE_EMBEDDED_COMPONENT_WANT

```c
NODE_EMBEDDED_COMPONENT_WANT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_EMBEDDED_COMPONENT = 1016000
```

定义用于启动EmbeddedAbility的want。支持属性设置。
作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | EmbeddedComponent的want参数。参数类型为[AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md)。默认值为nullptr。 |

## NODE_EMBEDDED_COMPONENT_OPTION

```c
NODE_EMBEDDED_COMPONENT_OPTION = 1016001
```

EmbeddedComponent的选项。支持属性设置。<br>
作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | EmbeddedComponent的选项列表，参数类型为[ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md)。 |
