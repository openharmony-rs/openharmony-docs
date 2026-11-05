# OH_AVRecorder_MetadataTemplate

```c
struct OH_AVRecorder_MetadataTemplate {...}
```

## Overview

Defines the basic template of metadata during audio and video recording. Metadata is organized in key-value pair format. This struct is applicable to scenarios where custom metadata (such as title, author, and description) needs to be added to the recording output, facilitating the classification, retrieval, and management of recorded files. You can use the [OH_AVRecorder_Prepare][OH_AVRecorder_Prepare](capi-avrecorder-h.md#oh_avrecorder_prepare) API of AVRecorder to set the metadata in this struct to the recording output file.

**Since**: 18

**Related module**: [AVRecorder](capi-others-avrecorder.md)

**Header file**: [avrecorder_base.h](capi-avrecorder-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *key | Metadata key.<br>**Since**: 18 |
| char *value | Metadata value.<br>**Since**: 18 |


