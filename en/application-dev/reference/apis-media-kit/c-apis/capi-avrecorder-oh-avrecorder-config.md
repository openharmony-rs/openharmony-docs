# OH_AVRecorder_Config

```c
typedef struct OH_AVRecorder_Config {...} OH_AVRecorder_Config
```

## Overview

The struct describes the AVRecorder configuration.

**Since**: 18

**Related module**: [AVRecorder](capi-avrecorder.md)

**Header file**: [avrecorder_base.h](capi-avrecorder-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_AVRecorder_AudioSourceType](capi-avrecorder-base-h.md#oh_avrecorder_audiosourcetype) audioSourceType | Indicates the recording audio source type |
| [OH_AVRecorder_VideoSourceType](capi-avrecorder-base-h.md#oh_avrecorder_videosourcetype) videoSourceType | Indicates the recording video source type |
| [OH_AVRecorder_Profile](capi-avrecorder-oh-avrecorder-profile.md) profile | Contains the audio and video encoding profile settings |
| char *url | Defines the file URL |
| [OH_AVRecorder_FileGenerationMode](capi-avrecorder-base-h.md#oh_avrecorder_filegenerationmode) fileGenerationMode | Specifies the file generation mode for recording output |
| [OH_AVRecorder_Metadata](capi-avrecorder-oh-avrecorder-metadata.md) metadata | Contains additional metadata for the recorded media |
| int32_t maxDuration | Set the longest duration allowed for current recording |


