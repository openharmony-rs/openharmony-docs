# ArkUI_NodeAttributeType (Accessibility Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the accessibility attribute types that can be set by ArkUI on the native side, including the accessibility text, description, mode, status, and information.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_ACCESSIBILITY_GROUP

```c
NODE_ACCESSIBILITY_GROUP = 62
```

Accessibility group. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | The value **1** means that the component and all its child components form an entire selectable component. In this case, the accessibility service will no longer be available for the content of its child components. The value is **1** or **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | The value **1** means that the component and all its child components form an entire selectable component. In this case, the accessibility service will no longer be available for the content of its child components. The value is **1** or **0**.|

## NODE_ACCESSIBILITY_TEXT

```c
NODE_ACCESSIBILITY_TEXT = 63
```

Accessibility text. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Accessibility text.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Accessibility text.|

## NODE_ACCESSIBILITY_MODE

```c
NODE_ACCESSIBILITY_MODE = 64
```

Accessibility mode. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Accessibility mode. The parameter type is [ArkUI_AccessibilityMode](capi-native-type-h.md#arkui_accessibilitymode).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Accessibility mode. The parameter type is [ArkUI_AccessibilityMode](capi-native-type-h.md#arkui_accessibilitymode).|

## NODE_ACCESSIBILITY_DESCRIPTION

```c
NODE_ACCESSIBILITY_DESCRIPTION = 65
```

Accessibility description. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Accessibility description.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Accessibility description.|

## NODE_ACCESSIBILITY_ID

```c
NODE_ACCESSIBILITY_ID = 87
```

Custom accessibility ID. This attribute can be obtained as required through APIs.<br>
The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br>

**Since**: 12


**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Custom accessibility ID.|

## NODE_ACCESSIBILITY_ACTIONS

```c
NODE_ACCESSIBILITY_ACTIONS = 88
```

Accessibility action type. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Accessibility action type. The parameter type is [ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Accessibility action type. The parameter type is [ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype).|

## NODE_ACCESSIBILITY_ROLE

```c
NODE_ACCESSIBILITY_ROLE = 89
```

Accessibility component role. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Accessibility component role. The parameter type is [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Accessibility component role. The parameter type is [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype).|

## NODE_ACCESSIBILITY_STATE

```c
NODE_ACCESSIBILITY_STATE = 90
```

Accessibility state. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .object | Accessibility state. The parameter type is [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Accessibility state. The parameter type is [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md).|

## NODE_ACCESSIBILITY_VALUE

```c
NODE_ACCESSIBILITY_VALUE = 91
```

Accessibility value. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .object | Accessibility value. The parameter type is [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Accessibility value. The parameter type is [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md).|
