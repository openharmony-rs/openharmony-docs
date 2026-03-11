# OH_DecodingOptions
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_DecodingOptions OH_DecodingOptions
```

## Overview

The OH_DecodingOptions struct describes the decoding options encapsulated at the native layer. The struct is used to set decoding options and is passed in as an input parameter for creating a PixelMap. For details, see [OH_ImageSourceNative_CreatePixelmap](capi-image-source-native-h.md#oh_imagesourcenative_createpixelmap).

The struct cannot be directly operated. Instead, functions must be called to create and release the struct and operate the fields in the struct.

To create an OH_DecodingOptions object, call [OH_DecodingOptions_Create](capi-image-source-native-h.md#oh_decodingoptions_create).

To release an OH_DecodingOptions object, call [OH_DecodingOptions_Release](capi-image-source-native-h.md#oh_decodingoptions_release).

The table below describes the content and operation mode of the OH_DecodingOptions struct.

| Field Type| Field Name| Field Description| Default Value| Getter Function| Setter Function|
| -------- | -------- | -------- | -------- | -------- | -------- |
| int32_t | pixelFormat | Pixel format.| RGBA_8888 | [OH_DecodingOptions_GetPixelFormat](capi-image-source-native-h.md#oh_decodingoptions_getpixelformat) | [OH_DecodingOptions_SetPixelFormat](capi-image-source-native-h.md#oh_decodingoptions_setpixelformat) |
| uint32_t | index | Index of the image to decode.| 0 | [OH_DecodingOptions_GetIndex](capi-image-source-native-h.md#oh_decodingoptions_getindex) | [OH_DecodingOptions_SetIndex](capi-image-source-native-h.md#oh_decodingoptions_setindex) |
| float | rotate | Rotation angle.| **0**, in degree (deg).| [OH_DecodingOptions_GetRotate](capi-image-source-native-h.md#oh_decodingoptions_getrotate) | [OH_DecodingOptions_SetRotate](capi-image-source-native-h.md#oh_decodingoptions_setrotate) |
| Image_Size | desiredSize | Desired output size.| Original image size.| [OH_DecodingOptions_GetDesiredSize](capi-image-source-native-h.md#oh_decodingoptions_getdesiredsize) | [OH_DecodingOptions_SetDesiredSize](capi-image-source-native-h.md#oh_decodingoptions_setdesiredsize) |
| Image_Region | desiredRegion | Region to decode.| Entire image.| [OH_DecodingOptions_GetDesiredRegion](capi-image-source-native-h.md#oh_decodingoptions_getdesiredregion) | [OH_DecodingOptions_SetDesiredRegion](capi-image-source-native-h.md#oh_decodingoptions_setdesiredregion) |
| int32_t | desiredDynamicRange | Desired dynamic range.| SDR |[OH_DecodingOptions_GetDesiredDynamicRange](capi-image-source-native-h.md#oh_decodingoptions_getdesireddynamicrange) | [OH_DecodingOptions_SetDesiredDynamicRange](capi-image-source-native-h.md#oh_decodingoptions_setdesireddynamicrange) |

**Since**: 12

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

**Header file**: [image_source_native.h](capi-image-source-native-h.md)
