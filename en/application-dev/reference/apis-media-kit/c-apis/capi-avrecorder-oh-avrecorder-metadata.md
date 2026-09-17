# OH_AVRecorder_Metadata

```c
typedef struct OH_AVRecorder_Metadata {...} OH_AVRecorder_Metadata
```

## Overview

The struct describes the metadata.

**Since**: 18

**Related module**: [AVRecorder](capi-avrecorder.md)

**Header file**: [avrecorder_base.h](capi-avrecorder-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *genre | The metadata to retrieve the content type or genre of the data source |
| char *videoOrientation | The metadata to retrieve the information about the video orientation, in degrees |
| [OH_AVRecorder_Location](capi-avrecorder-oh-avrecorder-location.md) location | The geographical location info of the video |
| [OH_AVRecorder_MetadataTemplate](capi-avrecorder-oh-avrecorder-metadatatemplate.md) customInfo | Custom parameter key-value map read from moov.meta.list |


