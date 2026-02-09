# OH_AVMetadataExtractor_FrameInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @wang-haizhou6-->
<!--Designer: @HmQQQ-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_AVMetadataExtractor_FrameInfo
```

## Overview

Defines the information about a frame extracted from a video.

**Since**: 23

**Related module**: [AVMetadataExtractor](capi-avmetadataextractor.md)

**Header file**: [avmetadata_extractor_base.h](capi-avmetadata-extractor-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int64_t requestTimeUs | Time when the user sends the request.|
| int64_t actualTimeUs | Time when the frame is actually extracted. If the extraction fails, the value is **-1**.|
| [OH_PixelmapNative*](../apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md) image | Frame image extracted from the video. If the extraction fails, the value is a null pointer.|
| [OH_AVMetadataExtractor_FetchState](capi-avmetadata-extractor-base-h.md#oh_avmetadataextractor_fetchstate) result | Result status of the frame extraction operation.|
