# VideoProcessing_ColorSpaceInfo

```c
struct VideoProcessing_ColorSpaceInfo {...}
```

## Overview

The struct describes the color space information of video processing.

**System capability**: SystemCapability.Multimedia.VideoProcessingEngine

**Since**: 12

**Related module**: [VideoProcessing](capi-others-videoprocessing.md)

**Header file**: [video_processing_types.h](capi-video-processing-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t metadataType | The metadata type of the video, see enum OH_NativeBuffer_MetadataType |
| int32_t colorSpace | The color space type of the video, see enum OH_NativeBuffer_ColorSpace |
| int32_t pixelFormat | The pixel format of the video, see enum OH_NativeBuffer_Format |


