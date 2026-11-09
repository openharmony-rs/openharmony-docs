# OH_AVRecorder_Config

```c
struct OH_AVRecorder_Config {...}
```

## Overview

Describes the AVRecorder configuration, which is used to set the audio source type, video source type, encoding configuration, output file URL, file generation mode, metadata, and maximum recording duration during audio and video recording. This struct is applicable to scenarios where custom recording configurations are required.

<!--Device-struct OH_AVRecorder_Config {...}--><!--Device-struct OH_AVRecorder_Config {...}-End-->

**Since**: 18

**Related module**: [AVRecorder](capi-media-kit-avrecorder.md)

**Header file**: [avrecorder_base.h](capi-avrecorder-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_AVRecorder_AudioSourceType](capi-avrecorder-base-h.md#oh_avrecorder_audiosourcetype) audioSourceType | Audio source type, which specifies the audio input source.<br>**Since**: 18 |
| [OH_AVRecorder_VideoSourceType](capi-avrecorder-base-h.md#oh_avrecorder_videosourcetype) videoSourceType | Video source type, which specifies the video input source.<br>**Since**: 18 |
| [OH_AVRecorder_Profile](capi-avrecorder-oh-avrecorder-profile.md) profile | Profile, including detailed parameters for audio and video recording, such as the encoding format, bitrate, and resolution.<br>**Since**: 18 |
| char *url | URL of the recording output file, in the format of **fd://xx**, where **xx** is the value of the file descriptor (FD), which must be a non-negative integer. This parameter is mandatory when the **fileGenerationMode** is created by the app. It is not required when the **fileGenerationMode** is created by the system. If the input URL is not in this format, the recording preparation fails. Ensure that the FD remains valid during recording to prevent recording exceptions caused by an invalid FD.<br>**Since**: 18 |
| [OH_AVRecorder_FileGenerationMode](capi-avrecorder-base-h.md#oh_avrecorder_filegenerationmode) fileGenerationMode | Mode for generating the recording output file. In recording scenarios where the output file URL needs to be customized, the mode of creating files by the app is applicable. In recording scenarios where the output file URL does not need to be specified, the mode of creating files by the system is applicable. In this mode, the app obtains the media resource file generated during recording by triggering the **OH_AVRecorder_OnUri** callback notification. The default value is the mode of creating files by the app.<br>**Since**: 18 |
| [OH_AVRecorder_Metadata](capi-avrecorder-oh-avrecorder-metadata.md) metadata | Metadata of the recorded media. This parameter is used to add descriptive attributes to the recorded file, such as genre, video rotation orientation, geographical location, and custom parameters. This parameter is left empty by default.<br>**Since**: 18 |
| int32_t maxDuration | Maximum recording duration, in seconds. If the value is less than or equal to 0, there is no duration limit. The default value is **0**. When the maximum recording duration is reached, the recording automatically stops.<br>**Since**: 18 |


