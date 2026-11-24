# OhosImageDecodingOps

```c
struct OhosImageDecodingOps {...}
```

## Overview

Defines the options for decoding the image source. It is used in [OH_ImageSource_CreatePixelMap](capi-image-source-mdk-h.md#oh_imagesource_createpixelmap) and [OH_ImageSource_CreatePixelMapList](capi-image-source-mdk-h.md#oh_imagesource_createpixelmaplist).

<!--Device-struct OhosImageDecodingOps {...}--><!--Device-struct OhosImageDecodingOps {...}-End-->

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-image-kit-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int8_t editable | Defines output pixel map editable.<br><!--Device-int8_t editable--><!--Device-int8_t editable-End--> |
| int32_t pixelFormat | Defines output pixel format.<br><!--Device-int32_t pixelFormat--><!--Device-int32_t pixelFormat-End--> |
| int32_t fitDensity | Defines decoding target pixel density.<br><!--Device-int32_t fitDensity--><!--Device-int32_t fitDensity-End--> |
| uint32_t index | Defines decoding index of image source.<br><!--Device-uint32_t index--><!--Device-uint32_t index-End--> |
| uint32_t sampleSize | Defines decoding sample size option.<br><!--Device-uint32_t sampleSize--><!--Device-uint32_t sampleSize-End--> |
| uint32_t rotate | Defines decoding rotate option.<br><!--Device-uint32_t rotate--><!--Device-uint32_t rotate-End--> |
| [struct OhosImageSize](capi-image-ohosimagesize.md) size | Defines decoding target pixel size of width and height.<br><!--Device-struct OhosImageSize size--><!--Device-struct OhosImageSize size-End--> |
| [struct OhosImageRegion](capi-image-ohosimageregion.md) region | Defines image source pixel region for decoding.<br><!--Device-struct OhosImageRegion region--><!--Device-struct OhosImageRegion region-End--> |


