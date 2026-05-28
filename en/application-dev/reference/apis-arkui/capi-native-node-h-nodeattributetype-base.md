# ArkUI_NodeAttributeType (Basic Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW; @wangyang2022; @zju_ljz-->
<!--Designer: @CCFFWW; @wangyang2022; @lanshouren-->
<!--Tester: @liuli0427; @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the basic attribute types that can be set by ArkUI on the native side, including the background, background image style, and component ID.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

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
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .string | Image address. In API version 22 and earlier versions, the value can be a network image resource address, local image resource address, Base64 string, or [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) resource, but cannot be the address of an animated image such as an [SVG](arkui-js/js-components-svg.md), GIF, or WebP image. In API version 23 and later versions, animated images of the WebP and GIF types are supported. Only the first frame of the animated image is displayed. Other types of animated images are not supported.|
| .value[0]?.i32 | Whether to repeat the image. This parameter is optional. The parameter type is [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat). The default value is **ARKUI_IMAGE_REPEAT_NONE**.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md). Either **.object** or **.string** must be set.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Image address. In API version 22 and earlier versions, the value can be a network image resource address, local image resource address, Base64 string, or PixelMap resource, but cannot be the address of an animated image such as an SVG, GIF, or WebP image. In API version 23 and later versions, animated images of the WebP and GIF types are supported. Only the first frame of the animated image is displayed. Other types of animated images are not supported.|
| .value[0].i32 | Whether the image is repeated. The parameter type is [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat).|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).|

## NODE_ID

```c
NODE_ID = 5
```

Component ID attribute, which can be set, reset, and obtained as required through APIs.<br>
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

## NODE_BACKGROUND_IMAGE_SIZE

```c
NODE_BACKGROUND_IMAGE_SIZE = 30
```

Background image size attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Width of the image. The value range is [0,+∞), and the unit is vp.|
| .value[1].f32 | Height of the image. The value range is [0,+∞), and the unit is vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Width of the image, in vp.|
| .value[1].f32 | Height of the image, in vp.|

## NODE_BACKGROUND_IMAGE_SIZE_WITH_STYLE

```c
NODE_BACKGROUND_IMAGE_SIZE_WITH_STYLE = 31
```

Background image size with style. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Size of the background image. The value is an enumerated value of [ArkUI_ImageSize](capi-native-type-h.md#arkui_imagesize).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Size of the background image. The value is an enumerated value of [ArkUI_ImageSize](capi-native-type-h.md#arkui_imagesize).|

## NODE_BACKGROUND_IMAGE_POSITION

```c
NODE_BACKGROUND_IMAGE_POSITION = 56
```

Position of the background image in the component, that is, the coordinates relative to the upper left corner of the component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Position along the x-axis, in px.|
| .value[1].f32 | Position along the y-axis, in px.|
| .value[2]?.i32 | Alignment mode. This parameter is optional. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment). The default value is **ARKUI_ALIGNMENT_TOP_START**. This parameter is supported since API version 21.|
| .value[3]?.i32 | Layout direction. This parameter is optional. The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction). The default value is **ARKUI_DIRECTION_AUTO**. In most scenarios, you are advised to set this parameter to **AUTO**, so that the system automatically handles the layout direction. If a fixed direction is required, set this parameter to **LTR** or **RTL**. This parameter is supported since API version 21.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Position along the x-axis, in px.|
| .value[1].f32 | Position along the y-axis, in px.|
| .value[2].i32 | Alignment mode. The parameter type is [ArkUI_Alignment](capi-native-type-h.md#arkui_alignment). This return value is supported since API version 21.|
| .value[3].i32 | Layout direction. The parameter type is [ArkUI_Direction](capi-native-type-h.md#arkui_direction). This return value is supported since API version 21.|

## NODE_RENDER_GROUP

```c
NODE_RENDER_GROUP = 80
```

Whether the component and its child components are rendered off the screen and then drawn together with its parent. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the component and its child components are rendered off the screen and then drawn together with its parent. The value **1** means that the component and its child components are rendered off the screen and then drawn together with its parent, and **0** means the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the component and its child components are rendered off the screen and then drawn together with its parent. The value **1** means that the component and its child components are rendered off the screen and then drawn together with its parent, and **0** means the opposite.|

## NODE_UNIQUE_ID

```c
NODE_UNIQUE_ID = 95
```

Component ID. This attribute can be obtained as required through APIs.<br>
The component ID is read-only and unique in a process.<br>

**Since**: 12

This API is supported since API version 12 and deprecated since API version 20. You are advised to use [OH_ArkUI_NodeUtils_GetNodeUniqueId](capi-native-node-h.md#oh_arkui_nodeutils_getnodeuniqueid) instead.

## NODE_CLICK_DISTANCE

```c
NODE_CLICK_DISTANCE = 97
```

Moving distance limit for the component-bound click gesture. This attribute can be set as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Allowed moving distance of a finger, in vp.|

## NODE_INSPECTOR_LABEL

```c
NODE_INSPECTOR_LABEL = 126
```

Inspector label, which helps you distinguish nodes of the same type to improve development, analysis, and debugging efficiency. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 26.0.0


**Parameters**

| Name| Description|
| -- | -- |
| .string | Content of the inspector label. If a null pointer is passed, the local call is invalid. An empty string is supported.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Content of the inspector label.|
