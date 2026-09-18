# ImageProcessing_ColorSpaceInfo

```c
typedef struct ImageProcessing_ColorSpaceInfo {...} ImageProcessing_ColorSpaceInfo
```

## Overview

The color space information is used for color space conversion capability query.

**Since**: 13

**Related module**: [ImageProcessing](capi-imageprocessing.md)

**Header file**: [image_processing_types.h](capi-image-processing-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t metadataType | define metadata type, {@link enum OH_Pixelmap_HdrMetadataKey} |
| int32_t colorSpace | define color space, {@link enum ColorSpaceName} |
| int32_t pixelFormat | define pixel format, {@link enum PIXEL_FORMAT} |


