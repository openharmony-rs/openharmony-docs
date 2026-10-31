# ArkUI_NodeAttributeType (General Attribute)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f31616e260099e81bbcddbe855b85fd9f463bdf7 translatedAt=2026-08-21T12:12:50.819Z pushedAt=2026-08-24T08:54:05.836Z -->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the general attribute types that can be set by ArkUI on the native side. It applies to scenarios where component style information needs to be dynamically set or obtained on the native side, allowing you to manage the component appearance in a unified manner through C APIs. The enumerated values are used as the attribute parameters of attribute operation APIs to specify the specific attribute type to be set, reset, or obtained, and work with the **ArkUI_AttributeItem** struct to pass attribute data. For details about the related attribute operation APIs, see [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute), [resetAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#resetattribute), and [getAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#getattribute).

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_WIDTH

```c
NODE_WIDTH = 0
```

Width attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Width, in vp, used to set the component width. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Width, in vp.|

## NODE_HEIGHT

```c
NODE_HEIGHT = 1
```

Height attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Height, in vp, used to set the height of the component. Negative values are not supported. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Height, in vp.|

## NODE_BACKGROUND_COLOR

```c
NODE_BACKGROUND_COLOR = 2
```

Background color attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format. For example, **0xFFFF0000** indicates red. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format. For example, **0xFFFF0000** indicates red. |

## NODE_BACKGROUND_IMAGE

```c
NODE_BACKGROUND_IMAGE = 3
```

Background image attribute, which can be set, reset, and obtained as required through APIs. After the attribute is reset, it is restored to the default state, in which no background image is displayed.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .string | Image address. In API version 22 and earlier, network image resource addresses, local image resource addresses, and Base64-format image addresses are supported, but [SVG](arkui-js/js-components-svg.md) images and animated images such as GIF and WebP are not supported. Since API version 23, animated images of the WebP and GIF types are newly supported, and the first frame of the animated image is displayed. Other types of animated images are not supported. |
| .value[0]?.i32 | Whether the image is repeated. This parameter is optional. The parameter type is [ArkUI_ImageRepeat](capi-image-h.md#arkui_imagerepeat). The default value is **ARKUI_IMAGE_REPEAT_NONE**. |
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set. If both are set, only one of them takes effect. |

**Returns**

| Type| Description|
| -- | -- |
| .string | Image address. In API version 22 and earlier, network image resource addresses, local image resource addresses, and Base64-format image addresses are supported, but animated images such as SVG, GIF, and WebP are not supported. Since API version 23, animated images of the WebP and GIF types are supported, and the first frame of the animated image is displayed. Other types of animated images are not supported. |
| .value[0].i32 | Whether the image is repeated. The parameter type is [ArkUI_ImageRepeat](capi-image-h.md#arkui_imagerepeat). |
| .object | **PixelMap** object. The type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** is used, and only one of them has a value. |