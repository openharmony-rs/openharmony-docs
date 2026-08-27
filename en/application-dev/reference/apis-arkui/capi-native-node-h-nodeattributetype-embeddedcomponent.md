# ArkUI_NodeAttributeType (EmbeddedComponent Attribute)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=ef5506642718b24289c6aa216632b7a5e19e795e translatedAt=2026-08-25T02:16:42.361Z pushedAt=2026-08-26T03:06:00.404Z -->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the **EmbeddedComponent** attribute types that can be set by ArkUI on the native side. It supports setting the **want** parameter for starting an EmbeddedAbility and runtime options such as controlling the UI display behavior of the EmbeddedAbility. It is applicable to scenarios where the attributes of an embedded component need to be set on the native side. **EmbeddedComponent** is applicable to scenarios where the UI pages provided by other Abilities (such as system settings and maps) need to be embedded in the current application page.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_EMBEDDED_COMPONENT_WANT

```c
NODE_EMBEDDED_COMPONENT_WANT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_EMBEDDED_COMPONENT = 1016000
```

**Want** used to launch an EmbeddedAbility. This attribute can be set. It is used in the following scenario: When an application needs to embed a specified Ability in the current page (such as embedding a system settings page or a map component), this attribute is used to specify the target Ability.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| .object | **Want** parameter for **EmbeddedComponent**, used to specify the target information required for launching EmbeddedAbility. The parameter type is [AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md). The default value is **nullptr**. |

## NODE_EMBEDDED_COMPONENT_OPTION

```c
NODE_EMBEDDED_COMPONENT_OPTION = 1016001
```

Runtime option of **EmbeddedComponent**, which is used to control the UI display behavior of the EmbeddedAbility. This attribute can be set.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| .object | List of options for **EmbeddedComponent**. The parameter type is [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md). The default value is **nullptr**. |