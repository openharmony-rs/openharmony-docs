# ArkUI_NodeAttributeType (EmbeddedComponent Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=33898b66eb6c0bf66810bb0d90faa36b55a4ad07 translatedAt=2026-11-18T08:46:51.874Z pushedAt=2026-11-19T02:08:47.684Z nl=1 -->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the **EmbeddedComponent** attribute types that can be set by ArkUI on the native side. It supports setting the **want** parameter for starting an EmbeddedUIExtensionAbility and running options such as the running exception callback (**onError**) and normal exit callback (**onTerminated**) of **EmbeddedComponent**. It applies to scenarios where the attributes of an embedded component need to be set on the native side. **EmbeddedComponent** is applicable to scenarios where the UI pages provided by an EmbeddedUIExtensionAbility of the current application (or one that meets the cross-application embedding permission conditions) need to be embedded in the current application page.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_EMBEDDED_COMPONENT_WANT

```c
NODE_EMBEDDED_COMPONENT_WANT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_EMBEDDED_COMPONENT = 1016000
```

**Want** used to launch an EmbeddedUIExtensionAbility. This attribute can be set. It is used in the following scenario: When an application needs to embed an EmbeddedUIExtensionAbility (of the same application or one that meets the cross-application embedding permission conditions) in the current page, this attribute is used to specify the target EmbeddedUIExtensionAbility.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| .object | **Want** parameter for **EmbeddedComponent**, used to specify the target information required for launching EmbeddedUIExtensionAbility. The parameter type is [AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md). The default value is **nullptr**. |

## NODE_EMBEDDED_COMPONENT_OPTION

```c
NODE_EMBEDDED_COMPONENT_OPTION = 1016001
```

Running option of **EmbeddedComponent**, which is used to set the running exception callback (**onError**) and normal exit callback (**onTerminated**) of **EmbeddedComponent**. This attribute can be set.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| .object | Running option for **EmbeddedComponent**. The parameter type is [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md). The default value is **nullptr**. |
