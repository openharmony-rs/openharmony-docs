# OhosImageRegion

```c
struct OhosImageRegion {...}
```

## Overview

Defines the region of the image source to decode. It is used in {@link OhosImageDecodingOps}, {@link OH_ImageSource_CreatePixelMap}, and<br>{@link OH_ImageSource_CreatePixelMapList}.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t x | X coordinate of the start point, in pixels. |
| int32_t y | Y coordinate of the start point, in pixels. |
| int32_t width | Width of the region, in pixels. |
| int32_t height | Height of the region, in pixels. |


