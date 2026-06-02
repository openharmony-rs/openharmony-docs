# ArkUI_NodeAttributeType (General Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022; @hehongyang3-->
<!--Designer: @piggyguy; @wangyang2022; @hehongyang3-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the general attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_WIDTH

```c
NODE_WIDTH = 0
```

Width attribute, which can be set, reset, and obtained as required through APIs.
The format of the **ArkUI_AttributeItem** parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Width, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Width, in vp.|

## NODE_HEIGHT

```c
NODE_HEIGHT = 1
```

Height attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the **ArkUI_AttributeItem** parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Height, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Height, in vp.|

## NODE_BACKGROUND_COLOR

```c
NODE_BACKGROUND_COLOR = 2
```

Background color attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the **ArkUI_AttributeItem** parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

## NODE_BACKGROUND_IMAGE

```c
NODE_BACKGROUND_IMAGE = 3
```

Background image attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the **ArkUI_AttributeItem** parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Image address. In API version 22 and earlier versions, the value can be a network image resource address, local image resource address, Base64 string, or [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) resource, but cannot be the address of an animated image such as an [SVG](arkui-js/js-components-svg.md), GIF, or WebP image. In API version 23 and later versions, animated images of the WebP and GIF types are supported. Only the first frame of the animated image is displayed. Other types of animated images are not supported.|
| .value[0]?.i32 | Whether to repeat the image. This parameter is optional. The parameter type is [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat). The default value is **ARKUI_IMAGE_REPEAT_NONE**.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Image address. In API version 22 and earlier versions, the value can be a network image resource address, local image resource address, Base64 string, or PixelMap resource, but cannot be the address of an animated image such as an SVG, GIF, or WebP image. In API version 23 and later versions, animated images of the WebP and GIF types are supported. Only the first frame of the animated image is displayed. Other types of animated images are not supported.|
| .value[0].i32 | Whether the image is repeated. The parameter type is [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat).|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).|
