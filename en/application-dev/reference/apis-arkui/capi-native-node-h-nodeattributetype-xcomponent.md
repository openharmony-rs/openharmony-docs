# ArkUI_NodeAttributeType (XComponent Attribute)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e2e8608c64e606248f00eb66f3b2d4805fae44da translatedAt=2026-08-25T02:25:16.979Z pushedAt=2026-08-27T01:28:19.364Z -->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the **XComponent** attribute types that can be set by ArkUI on the native side, including the component ID, component type, surface width and height, surface display area, and whether image analysis is supported. It applies to scenarios where the rendering area and behavior of the **XComponent** component need to be customized and obtained on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_XCOMPONENT_ID

```c
NODE_XCOMPONENT_ID = MAX_NODE_SCOPE_NUM * ARKUI_NODE_XCOMPONENT = 12000
```

ID of the **XComponent** component. This attribute can be set and obtained through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .string | ID of the **XComponent** component, used to uniquely identify the component. |

**Returns**

| Type| Description|
| -- | -- |
| .string | ID of the **XComponent** component, used to uniquely identify the component. |

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
| .value[0].i32 | Type of the **XComponent** component. The parameter type is [ArkUI_XComponentType](capi-xcomponent-h.md#arkui_xcomponenttype). For details about the specific enumerated values and their correspondence with numbers, see the enumeration definition. |

## NODE_XCOMPONENT_SURFACE_SIZE

```c
NODE_XCOMPONENT_SURFACE_SIZE = 12002
```

Size of the surface held by the **XComponent** component. This attribute can only be obtained through APIs.<br>
If you attempt to modify the size of the surface by using the [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) API, the setting does not take effect.<br>
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

Display area of the surface held by the **XComponent** component. This attribute can be set and obtained through APIs. It applies to scenarios where a partial area within the **XComponent** component needs to be specified for rendering, such as cropped video display and partial rendering in PiP mode.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | X-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.|
| .value[1].i32 | Y-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.|
| .value[2].i32 | Width of the surface display area, in px. The value must be a positive integer. The setting does not take effect when 0 or a negative number is passed. |
| .value[3].i32 | Height of the surface display area, in px. The value must be a positive integer. The setting does not take effect when 0 or a negative number is passed. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | X-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.|
| .value[1].i32 | Y-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.|
| .value[2].i32 | Width of the surface display area, in px. The value must be a non-negative integer. |
| .value[3].i32 | Height of the surface display area, in px.|

## NODE_XCOMPONENT_ENABLE_ANALYZER

```c
NODE_XCOMPONENT_ENABLE_ANALYZER = 12004
```

Whether to enable the image analyzer for the **XComponent** component. This attribute can be set and obtained as required through APIs. When enabled, content recognition and analysis can be performed on the image displayed in the component. It applies to scenarios such as real-time recognition in camera preview and image content understanding.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the image analyzer. `1` indicates enable the image analyzer, and `0` indicates the opposite. The default value is `0`. Values other than 0 and 1 are treated as `0`. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the image analyzer is enabled. `1` indicates that the image analyzer is supported, and `0` indicates the opposite. |