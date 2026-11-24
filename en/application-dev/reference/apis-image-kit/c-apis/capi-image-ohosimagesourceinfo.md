# OhosImageSourceInfo

```c
struct OhosImageSourceInfo {...}
```

## Overview

Defines the image source information, which is obtained by calling [OH_ImageSource_GetImageInfo](capi-image-source-mdk-h.md#oh_imagesource_getimageinfo).

<!--Device-struct OhosImageSourceInfo {...}--><!--Device-struct OhosImageSourceInfo {...}-End-->

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-image-kit-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t pixelFormat | Pixel format of the image source. It is set in [OH_ImageSource_Create](capi-image-source-mdk-h.md#oh_imagesource_create).<br><!--Device-int32_t pixelFormat--><!--Device-int32_t pixelFormat-End--> |
| int32_t colorSpace | Color space of the image source.<br><!--Device-int32_t colorSpace--><!--Device-int32_t colorSpace-End--> |
| int32_t alphaType | Alpha type of the image source.<br><!--Device-int32_t alphaType--><!--Device-int32_t alphaType-End--> |
| int32_t density | Image density of the image source. It is set in [OH_ImageSource_Create](capi-image-source-mdk-h.md#oh_imagesource_create).<br><!--Device-int32_t density--><!--Device-int32_t density-End--> |
| [struct OhosImageSize](capi-image-ohosimagesize.md) size | Pixel width and height of the image source.<br><!--Device-struct OhosImageSize size--><!--Device-struct OhosImageSize size-End--> |


