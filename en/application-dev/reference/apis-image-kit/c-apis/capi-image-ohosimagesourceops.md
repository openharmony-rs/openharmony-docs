# OhosImageSourceOps

```c
struct OhosImageSourceOps {...}
```

## Overview

Defines image source options information [OH_ImageSource_Create](capi-image-source-mdk-h.md#oh_imagesource_create) and [OH_ImageSource_CreateIncremental](capi-image-source-mdk-h.md#oh_imagesource_createincremental).

<!--Device-struct OhosImageSourceOps {...}--><!--Device-struct OhosImageSourceOps {...}-End-->

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-image-kit-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t density | Pixel density of the image source.<br><!--Device-int32_t density--><!--Device-int32_t density-End--> |
| int32_t pixelFormat | Image source pixel format, used to describe YUV buffer usually.<br><!--Device-int32_t pixelFormat--><!--Device-int32_t pixelFormat-End--> |
| [struct OhosImageSize](capi-image-ohosimagesize.md) size | Image source pixel size of width and height.<br><!--Device-struct OhosImageSize size--><!--Device-struct OhosImageSize size-End--> |


