# OH_Pixelmap_ImageInfo
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=7ede882c0a94b26c72c703e66553529436b49f4b translatedAt=2026-11-06T02:03:41.413Z pushedAt=2026-11-12T06:06:03.690Z nl=1 -->

```c
struct OH_Pixelmap_ImageInfo
```

## Overview

The OH_Pixelmap_ImageInfo struct encapsulates image pixel information at the native layer. It stores the width, height, row stride, pixel format, alpha type, and whether it is an HDR image, and is used to query Pixelmap properties at the native layer.

To create an OH_Pixelmap_ImageInfo object, call [OH_PixelmapImageInfo_Create](capi-pixelmap-native-h.md#oh_pixelmapimageinfo_create). After use, call [OH_PixelmapImageInfo_Release](capi-pixelmap-native-h.md#oh_pixelmapimageinfo_release) to release the resources. The two functions must be used in pairs; otherwise, memory leaks may occur.

The table below describes the content and operation mode of the OH_Pixelmap_ImageInfo struct.

| Field Type| Field Name| Field Description|Operation Function| Function Description|
| -------- | -------- | -------- | -------- | -------- |
| uint32_t | width | Image width, in px. | [OH_PixelmapImageInfo_GetWidth](capi-pixelmap-native-h.md#oh_pixelmapimageinfo_getwidth) | Obtains the image width. |
| uint32_t | height | Image height, in px. | [OH_PixelmapImageInfo_GetHeight](capi-pixelmap-native-h.md#oh_pixelmapimageinfo_getheight) | Obtains the image height. |
| uint32_t | rowStride | Row stride, which indicates the space occupied by each row of pixels in memory, in bytes. Affected by memory alignment, this value may be greater than the actual number of bytes of pixel data corresponding to the image width. | [OH_PixelmapImageInfo_GetRowStride](capi-pixelmap-native-h.md#oh_pixelmapimageinfo_getrowstride) | Obtains the row stride. |
| int32_t | pixelFormat | Pixel format, which indicates the color channel arrangement and bit depth information of the pixel data. For the value range, see [PIXEL_FORMAT](capi-pixelmap-native-h.md#pixel_format). | [OH_PixelmapImageInfo_GetPixelFormat](capi-pixelmap-native-h.md#oh_pixelmapimageinfo_getpixelformat) | Obtains the pixel format. |
| int32_t | alphaType | Alpha type. For details about the value, see [PIXELMAP_ALPHA_TYPE](capi-pixelmap-native-h.md#pixelmap_alpha_type). | [OH_PixelmapImageInfo_GetAlphaType](capi-pixelmap-native-h.md#oh_pixelmapimageinfo_getalphatype) | Obtains the alpha type. |
| bool | isHdr | Whether the PixelMap is high dynamic range (HDR). The value **true** indicates HDR, and **false** indicates non-HDR. | [OH_PixelmapImageInfo_GetDynamicRange](capi-pixelmap-native-h.md#oh_pixelmapimageinfo_getdynamicrange) | Checks whether the PixelMap is HDR. The value **true** indicates HDR, and **false** indicates non-HDR. |

**Since**: 12

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

**Header file**: [pixelmap_native.h](capi-pixelmap-native-h.md)