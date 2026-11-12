# ImageProcessing_ColorSpaceInfo

```c
typedef struct ImageProcessing_ColorSpaceInfo {...} ImageProcessing_ColorSpaceInfo
```

## Overview

The color space information is used for color space conversion capability query.

<!--Device-struct ImageProcessing_ColorSpaceInfo {...}--><!--Device-struct ImageProcessing_ColorSpaceInfo {...}-End-->

**System capability**: SystemCapability.Multimedia.VideoProcessingEngine

**Since**: 13

**Related module**: [ImageProcessing](capi-image-kit-imageprocessing.md)

**Header file**: [image_processing_types.h](capi-image-processing-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t metadataType | define metadata type, enum OH_Pixelmap_HdrMetadataKey |
| int32_t colorSpace | define color space, enum ColorSpaceName |
| int32_t pixelFormat | define pixel format, enum PIXEL_FORMAT |


