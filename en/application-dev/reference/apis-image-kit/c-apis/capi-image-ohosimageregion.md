# OhosImageRegion

```c
struct OhosImageRegion {...}
```

## Overview

Defines the region of the image source to decode. It is used in [OhosImageDecodingOps](capi-image-ohosimagedecodingops.md), [OH_ImageSource_CreatePixelMap](capi-image-source-mdk-h.md#oh_imagesource_createpixelmap), and [OH_ImageSource_CreatePixelMapList](capi-image-source-mdk-h.md#oh_imagesource_createpixelmaplist).

<!--Device-struct OhosImageRegion {...}--><!--Device-struct OhosImageRegion {...}-End-->

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-image-kit-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t x | X coordinate of the start point, in pixels.<br><!--Device-int32_t x--><!--Device-int32_t x-End--> |
| int32_t y | Y coordinate of the start point, in pixels.<br><!--Device-int32_t y--><!--Device-int32_t y-End--> |
| int32_t width | Width of the region, in pixels.<br><!--Device-int32_t width--><!--Device-int32_t width-End--> |
| int32_t height | Height of the region, in pixels.<br><!--Device-int32_t height--><!--Device-int32_t height-End--> |


