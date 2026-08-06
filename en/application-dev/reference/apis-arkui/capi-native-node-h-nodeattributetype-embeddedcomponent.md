# ArkUI_NodeAttributeType (EmbeddedComponent Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the **EmbeddedComponent** attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_EMBEDDED_COMPONENT_WANT

```c
NODE_EMBEDDED_COMPONENT_WANT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_EMBEDDED_COMPONENT = 1016000
```

Want used to launch an EmbeddedAbility. This attribute can be set.
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .object | Want parameter for **EmbeddedComponent**. The parameter type is [AbilityBase_Want](capi-arkui-nativemodule-abilitybase-want.md). The default value is **nullptr**.|

## NODE_EMBEDDED_COMPONENT_OPTION

```c
NODE_EMBEDDED_COMPONENT_OPTION = 1016001
```

Option of **EmbeddedComponent**. This attribute can be set.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .object | List of options for **EmbeddedComponent**. The parameter type is [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md).|
