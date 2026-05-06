# ArkUI_NodeAttributeType (Image Component Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43; @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attributes that can be set by ArkUI on the native side for image components including **Image** and **ImageAnimator**.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)


## NODE_IMAGE_SRC

```c
NODE_IMAGE_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE = 4000
```

Image address for the [Image](arkui-ts/ts-basic-components-image.md) component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Image address.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Image address.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).|

## NODE_IMAGE_OBJECT_FIT

```c
NODE_IMAGE_OBJECT_FIT = 4001
```

How the image is resized to fit its container. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | How the image is resized to fit its container, specified using the [ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit) enum.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | How the image is resized to fit its container, specified using the [ArkUI_ObjectFit](capi-native-type-h.md#arkui_objectfit) enum.|

## NODE_IMAGE_INTERPOLATION

```c
NODE_IMAGE_INTERPOLATION = 4002
```

Interpolation effect of the image. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Interpolation effect, which is specified using the [ArkUI_ImageInterpolation](capi-native-type-h.md#arkui_imageinterpolation) enum.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Interpolation effect, which is specified using the [ArkUI_ImageInterpolation](capi-native-type-h.md#arkui_imageinterpolation) enum.|

## NODE_IMAGE_OBJECT_REPEAT

```c
NODE_IMAGE_OBJECT_REPEAT = 4003
```

How the image is repeated. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | How the image is repeated, specified using the [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat) enum.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | How the image is repeated, specified using the [ArkUI_ImageRepeat](capi-native-type-h.md#arkui_imagerepeat) enum.|

## NODE_IMAGE_COLOR_FILTER

```c
NODE_IMAGE_COLOR_FILTER = 4004
```

Color filter of the image. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 to .value[19].f32| Filter matrix array.|
| .size | 5 x 4 filter array size.|
| .object | Pointer to the color filter. The parameter type is **OH_Drawing_ColorFilter**.<br>Either **.object** or **.size** must be set.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 to .value[19].f32| Filter matrix array.|
| .size | 5 x 4 filter array size.|
| .object | Pointer to the color filter. The parameter type is **OH_Drawing_ColorFilter**.|

## NODE_IMAGE_AUTO_RESIZE

```c
NODE_IMAGE_AUTO_RESIZE = 4005
```

Auto resize attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable auto resize. The default value is **false**. **true** to enable; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether auto resize is enabled.|

## NODE_IMAGE_ALT

```c
NODE_IMAGE_ALT = 4006
```

Placeholder image attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Address of the placeholder image.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set. Network images are not supported.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Address of the placeholder image.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).|

## NODE_IMAGE_DRAGGABLE

```c
NODE_IMAGE_DRAGGABLE = 4007
```

Whether the image is draggable. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the image is draggable. The value **true** means that the image is draggable.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the image is draggable.|

## NODE_IMAGE_RENDER_MODE

```c
NODE_IMAGE_RENDER_MODE = 4008
```

Image rendering mode. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Image rendering mode. The parameter type is [ArkUI_ImageRenderMode](capi-native-type-h.md#arkui_imagerendermode).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Image rendering mode. The parameter type is [ArkUI_ImageRenderMode](capi-native-type-h.md#arkui_imagerendermode).|

## NODE_IMAGE_FIT_ORIGINAL_SIZE

```c
NODE_IMAGE_FIT_ORIGINAL_SIZE = 4009
```

Whether the display size of an image follows the original size of the image source. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the display size of an image follows the original size of the image source. The value **1** indicates that the display size of an image follows the original size of the image source, and the value **0** indicates the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the display size of an image follows the original size of the image source. The value **1** indicates that the display size of an image follows the original size of the image source, and the value **0** indicates the opposite.|

## NODE_IMAGE_FILL_COLOR

```c
NODE_IMAGE_FILL_COLOR = 4010
```

Fill color to be superimposed on the image. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Fill color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Fill color, in 0xARGB format.|

## NODE_IMAGE_RESIZABLE

```c
NODE_IMAGE_RESIZABLE = 4011
```

Resizable image options.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Fixed distance (unchanged during stretching) from the left edge of the image. The unit is vp.|
| .value[1].f32 | Fixed distance (unchanged during stretching) from the top edge of the image. The unit is vp.|
| .value[2].f32 | Fixed distance (unchanged during stretching) from the right edge of the image. The unit is vp.|
| .value[3].f32 | Fixed distance (unchanged during stretching) from the bottom edge of the image. The unit is vp. When this attribute is used together with **NODE_IMAGE_ANTIALIASED**, the **NODE_IMAGE_ANTIALIASED** attribute setting does not take effect.|
| .object | The parameter type is [OH_Drawing_Lattice](../apis-arkgraphics2d/capi-drawing-oh-drawing-lattice.md).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Fixed distance (unchanged during stretching) from the left edge of the image. The unit is vp.|
| .value[1].f32 | Fixed distance (unchanged during stretching) from the top edge of the image. The unit is vp.|
| .value[2].f32 | Fixed distance (unchanged during stretching) from the right edge of the image. The unit is vp.|
| .value[3].f32 | Fixed distance (unchanged during stretching) from the bottom edge of the image. The unit is vp.|
| .object | The parameter type is [OH_Drawing_Lattice](../apis-arkgraphics2d/capi-drawing-oh-drawing-lattice.md).|

## NODE_IMAGE_SYNC_LOAD

```c
NODE_IMAGE_SYNC_LOAD = 4012
```

Synchronous image loading attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to load the image synchronously. The default value is **false**. **true**: Load the image synchronously. **false**: Load the image asynchronously.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the image is loaded synchronously.|

## NODE_IMAGE_SOURCE_SIZE

```c
NODE_IMAGE_SOURCE_SIZE = 4013
```

Decoding size of the image. This attribute works only when the target size is smaller than the source size. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Width for image decoding, in px.|
| .value[1].i32 | Height for image decoding, in px. If the value of any parameter is less than or equal to **0**, the attribute setting fails and [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) is returned, indicating a parameter error.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Width for image decoding, in px.|
| .value[1].i32 | Height for image decoding, in px.|

## NODE_IMAGE_IMAGE_MATRIX

```c
NODE_IMAGE_IMAGE_MATRIX = 4014
```

Transformation matrix of the image. This attribute can be set, reset, and obtained as required through APIs. Affine image transformation can be implemented using floating-point numbers or matrix objects.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .value[0...15].f32 | 4 x 4 matrix represented by a floating-point array with a length of 16. If the number of parameters is less than 16, the attribute setting fails, and [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) is returned, indicating a parameter error. If the number of parameters exceeds 16, only the first 16 data entries are used.|
| .object | The parameter type is [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0...15].f32 | 4 x 4 matrix represented by a floating-point array with a length of 16.|
| .object | The parameter type is [ArkUI_Matrix4](capi-arkui-nativemodule-arkui-matrix4.md).|

## NODE_IMAGE_MATCH_TEXT_DIRECTION

```c
NODE_IMAGE_MATCH_TEXT_DIRECTION = 4015
```

Whether the image follows the system language direction, displaying a mirrored effect in a right-to-left (RTL) language environments. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the image follows the system language direction. The default value is **false**. **true**: The image follows the system language direction. **false**: The image does not follow the system language direction.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | whether the image follows the system language direction. **true**: The image follows the system language direction. **false**: The image does not follow the system language direction.|

## NODE_IMAGE_COPY_OPTION

```c
NODE_IMAGE_COPY_OPTION = 4016
```

Image copy mode. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Image copy mode, specified using the [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions) enum. The default value is **ARKUI_COPY_OPTIONS_NONE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Image copy mode, specified using the [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions) enum.|

## NODE_IMAGE_ENABLE_ANALYZER

```c
NODE_IMAGE_ENABLE_ANALYZER = 4017
```

Whether to enable the AI analyzer, which supports subject recognition, text recognition, and object lookup. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the AI analyzer for images. The default value is **false**. **true** to enable; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the AI analyzer for images. **true** indicates that the AI analyzer is enabled; **false** otherwise.|

## NODE_IMAGE_DYNAMIC_RANGE_MODE

```c
NODE_IMAGE_DYNAMIC_RANGE_MODE = 4018
```

Dynamic range attribute for image display, specifying the dynamic range mode for image rendering (for example, SDR/HDR). This attribute can be set, reset, and obtained as required through APIs. It is used to match the capabilities of the display device and ensure accurate presentation of image brightness and colors.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Dynamic range mode, specified using the [ArkUI_DynamicRangeMode](capi-native-type-h.md#arkui_dynamicrangemode) enum. The default value is **ARKUI_DYNAMIC_RANGE_MODE_STANDARD**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Dynamic range mode, specified using the [ArkUI_DynamicRangeMode](capi-native-type-h.md#arkui_dynamicrangemode) enum.|

## NODE_IMAGE_HDR_BRIGHTNESS

```c
NODE_IMAGE_HDR_BRIGHTNESS = 4019
```

Brightness attribute of the image in HDR mode, used to control brightness parameters for high dynamic range display. This attribute can be set, reset, and obtained as required through APIs. It is used to ensure accurate presentation of details in the bright and dark areas of HDR images.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Brightness value. The value range is [0, 1]. Values less than 0 or greater than 1.0 are clamped to 1. **0**: The image is displayed at SDR brightness. **1**: The image is displayed at the highest allowed HDR brightness.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Brightness value. The value range is [0, 1].|

## NODE_IMAGE_ORIENTATION

```c
NODE_IMAGE_ORIENTATION = 4020
```

Display orientation of the image content. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Expected image content display orientation, specified using the [ArkUI_Orientation](capi-native-type-h.md#arkui_imagerotateorientation) enum. The default value is **ARKUI_ORIENTATION_UP**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Expected image content display orientation, specified using the [ArkUI_Orientation](capi-native-type-h.md#arkui_imagerotateorientation) enum.|

## NODE_IMAGE_SUPPORT_SVG2

```c
NODE_IMAGE_SUPPORT_SVG2 = 4021
```

Whether to enable the new SVG parsing capability, which allows you to set the scope of SVG parsing functionality support. This attribute can be set, reset, and obtained as required through APIs. After the **Image** component is created, the value of this attribute cannot be dynamically changed.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the new SVG parsing capability.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the new SVG parsing capability is enabled.|

## NODE_IMAGE_CONTENT_TRANSITION

```c
NODE_IMAGE_CONTENT_TRANSITION = 4022
```

Transition effect when the image changes. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .object | Custom transition animation. The parameter type is [ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Custom transition animation. The parameter type is [ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md).|

## NODE_IMAGE_ALT_PLACEHOLDER

```c
NODE_IMAGE_ALT_PLACEHOLDER  = 4023
```

Placeholder image during the loading process. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .string | Placeholder image address during the loading of the image component.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set. Network images are not supported.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Placeholder image address during the loading of the image component.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).|

## NODE_IMAGE_ALT_ERROR

```c
NODE_IMAGE_ALT_ERROR  = 4024
```

Placeholder image in the loading failure scenarios. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .string | Placeholder image address in the loading failure scenarios.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).<br>Either **.object** or **.string** must be set. Network images are not supported.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Placeholder image address in the loading failure scenarios.|
| .object | **PixelMap** object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).|

## NODE_IMAGE_ANTIALIASED

```c
NODE_IMAGE_ANTIALIASED = 4025
```

Whether to enable anti-aliasing for the edges of a bitmap image. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable anti-aliasing for the edges of a bitmap image. The default value is **false**. **true** to enable; **false** otherwise. This attribute does not take effect when used together with **NODE_IMAGE_RESIZABLE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether anti-aliasing is enabled for the edges of a bitmap image. **true** means enabled; **false** otherwise.|

## NODE_IMAGE_ANIMATOR_IMAGES

```c
NODE_IMAGE_ANIMATOR_IMAGES = ARKUI_NODE_IMAGE_ANIMATOR * MAX_NODE_SCOPE_NUM = 19000
```

Image frame information set of the frame animation component. Dynamic update is not supported. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .size | Number of image frames.|
| .object | Image frame array. The parameter type is [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md).|

**Returns**

| Type| Description|
| -- | -- |
| .size | Number of image frames.|
| .object | Image frame array. The parameter type is [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md).|

## NODE_IMAGE_ANIMATOR_STATE

```c
NODE_IMAGE_ANIMATOR_STATE = 19001
```

Playback status of the frame-by-frame animation. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Playback state of the frame-by-frame animation. The parameter type is [ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus). The default state is initial.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Playback state of the frame-by-frame animation. The parameter type is [ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus).|

## NODE_IMAGE_ANIMATOR_DURATION

```c
NODE_IMAGE_ANIMATOR_DURATION = 19002
```

Playback duration of the frame-by-frame animation. This attribute does not take effect when a separate duration is set for any of the image frames. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Playback duration, in milliseconds. The default value is **1000**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Playback duration, in milliseconds. The default value is **1000**.|

## NODE_IMAGE_ANIMATOR_REVERSE

```c
NODE_IMAGE_ANIMATOR_REVERSE = 19003
```

Playback direction of the frame-by-frame animation. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Playback direction. The value **0** indicates that images are played from the first one to the last one, and **1** indicates that images are played from the last one to the first one. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Playback direction. The value **0** indicates that images are played from the first one to the last one, and **1** indicates that images are played from the last one to the first one.|

## NODE_IMAGE_ANIMATOR_FIXED_SIZE

```c
NODE_IMAGE_ANIMATOR_FIXED_SIZE = 19004
```

Whether the image size is fixed at the component size. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the image size is fixed at the component size. The value **1** indicates that the image size is fixed at the component size. The value **0** indicates that the **width**, **height**, **top**, and **left** attributes of each image must be set separately. The default value is **1**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the image size is fixed at the component size. The value **1** indicates that the image size is fixed at the component size. The value **0** indicates that the **width**, **height**, **top**, and **left** attributes of each image must be set separately.|

## NODE_IMAGE_ANIMATOR_FILL_MODE

```c
NODE_IMAGE_ANIMATOR_FILL_MODE = 19005
```

Status before and after execution of the frame-by-frame animation in the current playback direction. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Status before and after execution of the frame-by-frame animation in the current playback direction. The parameter type is [ArkUI_AnimationFillMode](capi-native-type-h.md#arkui_animationfillmode). The default value is **ARKUI_ANIMATION_FILL_MODE_FORWARDS**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Status before and after execution of the frame-by-frame animation in the current playback direction. The parameter type is [ArkUI_AnimationFillMode](capi-native-type-h.md#arkui_animationfillmode).|

## NODE_IMAGE_ANIMATOR_ITERATION

```c
NODE_IMAGE_ANIMATOR_ITERATION = 19006
```

Number of times that the frame-by-frame animation is played. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Number of times that the animation is played.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of times that the animation is played.|
