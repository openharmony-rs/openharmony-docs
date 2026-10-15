# Image

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_IMAGE_SRC

```c
NODE_IMAGE_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE
```

**Description**

Defines the image source of the <Image> component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: image source.</li> <li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md). Either .string or .object must be set.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: image source.</li> <li>.object: The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).</li> </ul>

**Since**: 12

### NODE_IMAGE_OBJECT_FIT

```c
NODE_IMAGE_OBJECT_FIT
```

**Description**

How the image is resized to fit its container. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: image filling effect. The value is an enumerated value of [ArkUI_ObjectFit](capi-image-h.md#arkui_objectfit).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: image filling effect. The value is an enumerated value of [ArkUI_ObjectFit](capi-image-h.md#arkui_objectfit).</li> </ul>

**Since**: 12

### NODE_IMAGE_INTERPOLATION

```c
NODE_IMAGE_INTERPOLATION
```

**Description**

Interpolation effect of the image. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: interpolation effect. The value is an enumerated value of [ArkUI_ImageInterpolation](capi-image-h.md#arkui_imageinterpolation).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: interpolation effect. The value is an enumerated value of [ArkUI_ImageInterpolation](capi-image-h.md#arkui_imageinterpolation).</li> </ul>

**Since**: 12

### NODE_IMAGE_OBJECT_REPEAT

```c
NODE_IMAGE_OBJECT_REPEAT
```

**Description**

How the image is repeated. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: image repetition style. The value is an enumerated value of [ArkUI_ImageRepeat](capi-image-h.md#arkui_imagerepeat).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: image repetition style. The value is an enumerated value of [ArkUI_ImageRepeat](capi-image-h.md#arkui_imagerepeat).</li> </ul>

**Since**: 12

### NODE_IMAGE_COLOR_FILTER

```c
NODE_IMAGE_COLOR_FILTER
```

**Description**

Color filter of the image. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32 to .value[19].f32: filter matrix array.</li> <li>.size: 5 x 4 filter array size.</li> <li>.object: color filter pointer. The parameter type is <b>OH_Drawing_ColorFilter</b>. Either <b>.object</b> or <b>.size</b> must be set.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32 to .value[19].f32: filter matrix array.</li> <li>.size: 5 x 4 filter array size.</li> <li>.object: color filter pointer. The parameter type is <b>OH_Drawing_ColorFilter</b>.</li> </ul>

**Since**: 12

### NODE_IMAGE_AUTO_RESIZE

```c
NODE_IMAGE_AUTO_RESIZE
```

**Description**

Auto resize attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable auto resize. The default value is <b>false</b>. <b>true</b> to enable; <b>false</b> otherwise.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether auto resize is enabled.</li> </ul>

**Since**: 12

### NODE_IMAGE_ALT

```c
NODE_IMAGE_ALT
```

**Description**

Placeholder image address attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: address of the placeholder image.</li> <li>.object: <b>PixelMap</b> object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md). Either <b>.object</b> or <b>.string</b> must be set. Network images are not supported.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: address of the placeholder image.</li> <li>.object: <b>PixelMap</b> object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).</li> </ul>

**Since**: 12

### NODE_IMAGE_DRAGGABLE

```c
NODE_IMAGE_DRAGGABLE
```

**Description**

Whether the image is draggable. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the image is draggable. The value <b>true</b> means that the image is draggable.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the image is draggable.</li> </ul>

**Since**: 12

### NODE_IMAGE_RENDER_MODE

```c
NODE_IMAGE_RENDER_MODE
```

**Description**

Image rendering mode. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: image rendering mode. The value is an enumerated value of [ArkUI_ImageRenderMode](capi-image-h.md#arkui_imagerendermode).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: image rendering mode. The value is an enumerated value of [ArkUI_ImageRenderMode](capi-image-h.md#arkui_imagerendermode).</li> </ul>

**Since**: 12

### NODE_IMAGE_FIT_ORIGINAL_SIZE

```c
NODE_IMAGE_FIT_ORIGINAL_SIZE
```

**Description**

Whether the display size of an image follows the original size of the image source. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the display size of an image follows the original size of the image source. The value <b>1</b> indicates that the display size of an image follows the original size of the image source, and the value <b>0</b> indicates the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the display size of an image follows the original size of the image source. The value <b>1</b> indicates that the display size of an image follows the original size of the image source, and the value <b>0</b> indicates the opposite.</li> </ul>

**Since**: 12

### NODE_IMAGE_FILL_COLOR

```c
NODE_IMAGE_FILL_COLOR
```

**Description**

Fill color to be superimposed on the image. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: fill color, in 0xARGB format. For example, <b>0xFFFF0000</b> indicates red.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: fill color, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_IMAGE_RESIZABLE

```c
NODE_IMAGE_RESIZABLE
```

**Description**

Resizable image options.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: fixed distance (unchanged during stretching) from the left edge of the image. The unit is vp.</li> <li>.value[1].f32: fixed distance (unchanged during stretching) from the top edge of the image. The unit is vp.</li> <li>.value[2].f32: fixed distance (unchanged during stretching) from the right edge of the image. The unit is vp.</li> <li>.value[3].f32: fixed distance (unchanged during stretching) from the bottom edge of the image. The unit is vp. When this attribute is used together with <b>NODE_IMAGE_ANTIALIASED</b>, the <b>NODE_IMAGE_ANTIALIASED</b> attribute setting does not take effect.</li> <li>.object: The parameter type is [OH_Drawing_Lattice](../../apis-arkgraphics2d/c-apis/capi-drawing-oh-drawing-lattice.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: fixed distance (unchanged during stretching) from the left edge of the image. The unit is vp.</li> <li>.value[1].f32: fixed distance (unchanged during stretching) from the top edge of the image. The unit is vp.</li> <li>.value[2].f32: fixed distance (unchanged during stretching) from the right edge of the image. The unit is vp.</li> <li>.value[3].f32: fixed distance (unchanged during stretching) from the bottom edge of the image. The unit is vp.</li> <li>.object: The parameter type is [OH_Drawing_Lattice](../../apis-arkgraphics2d/c-apis/capi-drawing-oh-drawing-lattice.md).</li> </ul>

**Since**: 12

### NODE_IMAGE_SYNC_LOAD

```c
NODE_IMAGE_SYNC_LOAD = 4012
```

**Description**

Synchronous image loading attribute, which can be set, reset, and obtained as required through APIs. The [NODE_IMAGE_ALT](capi-native-node-h.md#arkui_nodeattributetype) placeholder image is always loaded asynchronously, and <b>syncLoad</b> does not take effect on it.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to load the image synchronously. The default value is <b>false</b>. <b>true</b>: Load the image synchronously. <b>false</b>: Load the image asynchronously.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the image is loaded synchronously.</li> </ul>

**Since**: 20

### NODE_IMAGE_SOURCE_SIZE

```c
NODE_IMAGE_SOURCE_SIZE = 4013
```

**Description**

Decoding size of the image. This attribute works only when the target size is smaller than the source size. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: width for image decoding, in px.</li> <li>.value[1].i32: height for image decoding, in px. If the value of any parameter is less than or equal to 0, the attribute setting fails and ARKUI_ERROR_CODE_PARAM_INVALID is returned, indicating a parameter error.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: width for image decoding, in px.</li> <li>.value[1].i32: height for image decoding, in px.</li> </ul>

**Since**: 21

### NODE_IMAGE_IMAGE_MATRIX

```c
NODE_IMAGE_IMAGE_MATRIX = 4014
```

**Description**

Transformation matrix of the image. This attribute can be set, reset, and obtained as required through APIs. Affine image transformation can be implemented using floating-point numbers.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0...15].f32: 4 x 4 matrix represented by a floating-point array with a length of 16. If the number of parameters is less than 16, the attribute setting fails, and ARKUI_ERROR_CODE_PARAM_INVALID is returned. If the number of parameters exceeds 16, only the first 16 data entries are used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0...15].f32: 4 x 4 matrix represented by a floating-point array with a length of 16.</li> </ul>

**Since**: 21

### NODE_IMAGE_MATCH_TEXT_DIRECTION

```c
NODE_IMAGE_MATCH_TEXT_DIRECTION = 4015
```

**Description**

Whether the image follows the system language direction, displaying a mirrored effect in a right-to-left (RTL) language environments. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the image follows the system language direction. The default value is <b>false</b>. <b>true</b>: The image follows the system language direction. <b>false</b>: The image does not follow the system language direction.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the image follows the system language direction. <b>true</b>: The image follows the system language direction. <b>false</b>: The image does not follow the system language direction.</li> </ul>

**Since**: 21

### NODE_IMAGE_COPY_OPTION

```c
NODE_IMAGE_COPY_OPTION = 4016
```

**Description**

Image copy mode. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: image copy mode, specified using the [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions) enum. The default value is <b>ARKUI_COPY_OPTIONS_NONE</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: image copy mode, specified using the [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions) enum.</li> </ul>

**Since**: 21

### NODE_IMAGE_ENABLE_ANALYZER

```c
NODE_IMAGE_ENABLE_ANALYZER = 4017
```

**Description**

Whether to enable the AI analyzer, which supports subject recognition, text recognition, and object lookup. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable the AI analyzer for images. The default value is <b>false</b>. <b>true</b> to enable; <b>false</b> otherwise.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the AI analyzer is enabled for images. <b>true</b> indicates that the AI analyzer is enabled; <b>false</b> otherwise.</li> </ul>

**Since**: 21

### NODE_IMAGE_DYNAMIC_RANGE_MODE

```c
NODE_IMAGE_DYNAMIC_RANGE_MODE = 4018
```

**Description**

Dynamic range attribute for image display, specifying the dynamic range mode for image rendering (for example, SDR/HDR). This attribute can be set, reset, and obtained as required through APIs. It is used to match the capabilities of the display device and ensure accurate presentation of image brightness and colors.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: dynamic range mode, specified using [ArkUI_DynamicRangeMode](capi-image-h.md#arkui_dynamicrangemode). The default value is <b>ARKUI_DYNAMIC_RANGE_MODE_STANDARD</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: dynamic range mode, specified using [ArkUI_DynamicRangeMode](capi-image-h.md#arkui_dynamicrangemode).</li> </ul>

**Since**: 21

### NODE_IMAGE_HDR_BRIGHTNESS

```c
NODE_IMAGE_HDR_BRIGHTNESS = 4019
```

**Description**

Brightness attribute of the image in HDR mode, used to control brightness parameters for high dynamic range display. This attribute can be set, reset, and obtained as required through APIs. It is used to ensure accurate presentation of details in the bright and dark areas of HDR images.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: brightness value. The value range is [0, 1]. Values less than 0 or greater than 1.0 are clamped to 1. <b>0</b>: The image is displayed at SDR brightness. <b>1</b>: The image is displayed at the highest allowed HDR brightness.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: brightness value. The value range is [0, 1].</li> </ul>

**Since**: 21

### NODE_IMAGE_ORIENTATION

```c
NODE_IMAGE_ORIENTATION = 4020
```

**Description**

Display orientation of the image content. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: expected image content display orientation, specified using [ArkUI_ImageRotateOrientation](capi-image-h.md#arkui_imagerotateorientation). The default value is <b>ARKUI_ORIENTATION_UP</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: expected image content display orientation, specified using [ArkUI_ImageRotateOrientation](capi-image-h.md#arkui_imagerotateorientation).</li> </ul>

**Since**: 21

### NODE_IMAGE_SUPPORT_SVG2

```c
NODE_IMAGE_SUPPORT_SVG2 = 4021
```

**Description**

Whether to enable the new SVG parsing capability, which allows you to set the scope of SVG parsing functionality support. This attribute can be set, reset, and obtained as required through APIs. After the <b>Image</b> component is created, the value of this attribute cannot be dynamically changed.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable the new SVG parsing capability.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the new SVG parsing capability is enabled.</li> </ul>

**Since**: 21

### NODE_IMAGE_CONTENT_TRANSITION

```c
NODE_IMAGE_CONTENT_TRANSITION = 4022
```

**Description**

Transition effect when the image changes. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: custom transition animation. The parameter type is [ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: custom transition animation. The parameter type is [ArkUI_ContentTransitionEffect](capi-arkui-nativemodule-arkui-contenttransitioneffect.md).</li> </ul>

**Since**: 21

### NODE_IMAGE_ALT_PLACEHOLDER

```c
NODE_IMAGE_ALT_PLACEHOLDER = 4023
```

**Description**

Placeholder image during the loading process. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: placeholder image address during the loading of the image component.</li> <li>.object: <b>PixelMap</b> object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md). Either <b>.object</b> or <b>.string</b> must be set. Network images are not supported.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: placeholder image address during the loading of the image component.</li> <li>.object: <b>PixelMap</b> object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).</li> </ul>

**Since**: 22

### NODE_IMAGE_ALT_ERROR

```c
NODE_IMAGE_ALT_ERROR = 4024
```

**Description**

Placeholder image in the loading failure scenarios. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: placeholder image address in the loading failure scenarios.</li> <li>.object: <b>PixelMap</b> object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md). Either <b>.object</b> or <b>.string</b> must be set. Network images are not supported.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: placeholder image address in the loading failure scenarios.</li> <li>.object: <b>PixelMap</b> object. The parameter type is [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md).</li> </ul>

**Since**: 22

### NODE_IMAGE_ANTIALIASED

```c
NODE_IMAGE_ANTIALIASED = 4025
```

**Description**

Whether to enable anti-aliasing for the edges of a bitmap image. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable anti-aliasing for the edges of a bitmap image. The default value is <b>false</b>. <b>true</b> to enable; <b>false</b> otherwise. This attribute does not take effect when used together with <b>NODE_IMAGE_RESIZABLE</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether anti-aliasing is enabled for the edges of a bitmap image. <b>true</b> means enabled; <b>false</b> otherwise.</li> </ul>

**Since**: 23


