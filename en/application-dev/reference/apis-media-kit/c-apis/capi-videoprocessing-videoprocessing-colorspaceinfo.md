# VideoProcessing_ColorSpaceInfo

```c
typedef struct VideoProcessing_ColorSpaceInfo {...} VideoProcessing_ColorSpaceInfo
```

## Overview

Video color space information structure of querying if video color space conversion is supported.

**Since**: 12

**Related module**: [VideoProcessing](capi-videoprocessing.md)

**Header file**: [video_processing_types.h](capi-video-processing-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t metadataType | The metadata type of the video, see {@link enum OH_NativeBuffer_MetadataType} |
| int32_t colorSpace | The color space type of the video, see {@link enum OH_NativeBuffer_ColorSpace} |
| int32_t pixelFormat | The pixel format of the video, see {@link enum OH_NativeBuffer_Format} |


