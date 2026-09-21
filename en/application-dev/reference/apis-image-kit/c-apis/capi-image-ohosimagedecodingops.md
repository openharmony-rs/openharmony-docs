# OhosImageDecodingOps

```c
struct OhosImageDecodingOps {...}
```

## Overview

Defines the options for decoding the image source. It is used in {@link OH_ImageSource_CreatePixelMap} and {@link OH_ImageSource_CreatePixelMapList}.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Since**: 10

**Related module**: [Image](capi-image.md)

**Header file**: [image_source_mdk.h](capi-image-source-mdk-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int8_t editable | Defines output pixel map editable. |
| int32_t pixelFormat | Defines output pixel format. |
| int32_t fitDensity | Defines decoding target pixel density. |
| uint32_t index | Defines decoding index of image source. |
| uint32_t sampleSize | Defines decoding sample size option. |
| uint32_t rotate | Defines decoding rotate option. |
| struct OhosImageSize size | Defines decoding target pixel size of width and height. |
| struct [OhosImageRegion](capi-image-ohosimageregion.md) region | Defines image source pixel region for decoding. |


