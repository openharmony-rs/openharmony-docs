# OH_AVRecorder_Profile

```c
typedef struct OH_AVRecorder_Profile {...} OH_AVRecorder_Profile
```

## Overview

The struct describes the parameters used for audio and video recording.

**Since**: 18

**Related module**: [AVRecorder](capi-avrecorder.md)

**Header file**: [avrecorder_base.h](capi-avrecorder-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t audioBitrate | Indicates the audio bitrate, in bit/s |
| int32_t audioChannels | Indicates the number of audio channels |
| [OH_AVRecorder_CodecMimeType](capi-avrecorder-base-h.md#oh_avrecorder_codecmimetype) audioCodec | Indicates the audio encoding format |
| int32_t audioSampleRate | Indicates the audio sampling rate, in Hz |
| [OH_AVRecorder_ContainerFormatType](capi-avrecorder-base-h.md#oh_avrecorder_containerformattype) fileFormat | Indicates the output file format |
| int32_t videoBitrate | Indicates the video bitrate, in bit/s |
| [OH_AVRecorder_CodecMimeType](capi-avrecorder-base-h.md#oh_avrecorder_codecmimetype) videoCodec | Indicates the video encoding format |
| int32_t videoFrameWidth | Indicates the video width, in px |
| int32_t videoFrameHeight | Indicates the video height, in px |
| int32_t videoFrameRate | Indicates the video frame rate, in fps |
| bool isHdr | Whether to record HDR video |
| bool enableTemporalScale | Whether to encode the video in temporal scale mode |


