# OhosImageSourceOps

```c
struct OhosImageSourceOps {...}
```

## Overview

Defines image source options information [OH_ImageSource_Create](capi-image-source-mdk-h.md#oh_imagesource_create) and [OH_ImageSource_CreateIncremental](capi-image-source-mdk-h.md#oh_imagesource_createincremental).

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t density | Pixel density of the image source. |
| int32_t pixelFormat | Image source pixel format, used to describe YUV buffer usually. |
| struct OhosImageSize size | Image source pixel size of width and height. |


