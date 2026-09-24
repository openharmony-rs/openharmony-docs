# OhosImageSourceInfo

```c
struct OhosImageSourceInfo {...}
```

## Overview

Defines the image source information, which is obtained by calling {@link OH_ImageSource_GetImageInfo}.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t pixelFormat | Pixel format of the image source. It is set in {@link OH_ImageSource_Create}. |
| int32_t colorSpace | Color space of the image source. |
| int32_t alphaType | Alpha type of the image source. |
| int32_t density | Image density of the image source. It is set in {@link OH_ImageSource_Create}. |
| struct OhosImageSize size | Pixel width and height of the image source. |


