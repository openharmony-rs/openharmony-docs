# ArkUI_NodeAttributeType (XComponent Attribute)
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

Enumerates the **XComponent** attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_XCOMPONENT_ID

```c
NODE_XCOMPONENT_ID = MAX_NODE_SCOPE_NUM * ARKUI_NODE_XCOMPONENT = 12000
```

ID of the **XComponent** component. This attribute can be set and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .string | Component ID.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Component ID.|

## NODE_XCOMPONENT_TYPE

```c
NODE_XCOMPONENT_TYPE = 12001
```

Type of the **XComponent** component. This attribute is read-only.<br>
The type of the **XComponent** component must be explicitly set during creation using **ARKUI_NODE_XCOMPONENT** or **ARKUI_NODE_XCOMPONENT_TEXTURE** in [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype), and cannot be modified afterward.<br>
Attempting to change the type through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) will cause rendering exceptions.<br>
The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br>

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Type of the **XComponent** component. The parameter type is [ArkUI_XComponentType](capi-xcomponent-h.md#arkui_xcomponenttype).|

## NODE_XCOMPONENT_SURFACE_SIZE

```c
NODE_XCOMPONENT_SURFACE_SIZE = 12002
```

Size of the **XComponent** component. This attribute is read-only.<br>
Attempting to modify the size through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) will have no effect.<br>
The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br>

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Width, in px.|
| .value[1].u32 | Height, in px.|


## NODE_XCOMPONENT_SURFACE_RECT

```c
NODE_XCOMPONENT_SURFACE_RECT = 12003
```

Display area of the surface held by the **XComponent** component.This attribute can be set and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | X-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.|
| .value[1].i32 | Y-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.|
| .value[2].i32 | Width of the surface display area, in px.|
| .value[3].i32 | Height of the surface display area, in px.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | X-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.|
| .value[1].i32 | Y-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.|
| .value[2].i32 | Width of the surface display area, in px.|
| .value[3].i32 | Height of the surface display area, in px.|

## NODE_XCOMPONENT_ENABLE_ANALYZER

```c
NODE_XCOMPONENT_ENABLE_ANALYZER = 12004
```

Whether to enable the image analyzer for the **XComponent** component. This attribute can be set and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the image analyzer. **1**: enable the image analyzer. **0**: disable the image analyzer. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the image analyzer is enabled. **1**: The image analyzer is enabled. **0**: The image analyzer is disabled. The default value is **0**.|
