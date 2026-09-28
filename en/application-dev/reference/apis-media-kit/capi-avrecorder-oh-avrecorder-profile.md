# OH_AVRecorder_Profile
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_dyOv3Sds-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->

```c
typedef struct OH_AVRecorder_Profile {/* For details about the member variables, see the summary.*/} OH_AVRecorder_Profile
```

## Overview

Defines a struct for the parameters used for audio and video recording. By configuring parameters such as the audio/video encoding format, bitrate, sampling rate, frame rate, resolution, container format, HDR recording, and whether to enable temporally scalable video encoding, you can flexibly control the recording quality and file size. This is applicable to scenarios where you need to customize the recording quality, select the recording content type (audio-only, video-only, or both), and enable HDR recording or temporally scalable video encoding.

You can choose to record only audio, only video, or both by setting the parameters.

1. When **audioBitrate** or **audioChannels** is set to **0**, audio recording is disabled.
2. When **videoFrameWidth** or **videoFrameHeight** is set to **0**, video recording is disabled.

For details about the value range of each parameter, see [AVRecorderProfile](arkts-apis-media-i.md#avrecorderprofile9).

**Since**: 18

**Related module**: [AVRecorder](capi-avrecorder.md)

**Header file**: [avrecorder_base.h](capi-avrecorder-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t audioBitrate | Audio encoding bit rate, in bit/s. A larger value indicates better audio quality but a larger file size. For details about the value range, see [AVRecorderProfile](arkts-apis-media-i.md#avrecorderprofile9). The default value is **0**, indicating that audio is not recorded. If the value is beyond the valid range, the recording fails.|
| int32_t audioChannels | Number of audio channels. A larger value indicates stronger audio spatiality but a larger file size. For details about the value range, see [AVRecorderProfile](arkts-apis-media-i.md#avrecorderprofile9). The default value is **0**, indicating that audio is not recorded. If the value is beyond the valid range, the recording fails.|
| [OH_AVRecorder_CodecMimeType](capi-avrecorder-base-h.md#oh_avrecorder_codecmimetype) audioCodec | MIME type of the audio encoder. Different types of audio encoders have different audio quality, file size, and compatibility. For details about the encoder types, see [OH_AVRecorder_CodecMimeType](capi-avrecorder-base-h.md#oh_avrecorder_codecmimetype). This parameter is valid only when audio is being recorded.|
| int32_t audioSampleRate | Audio sampling rate. The unit is Hz. For details about the value range, see [AVRecorderProfile](arkts-apis-media-i.md#avrecorderprofile9). A higher sampling rate indicates better audio quality but a larger file size. If the value is beyond the valid range, the recording fails. The default value is **0**. This parameter is valid only when audio is being recorded.|
| [OH_AVRecorder_ContainerFormatType](capi-avrecorder-base-h.md#oh_avrecorder_containerformattype) fileFormat | Container format. The container format determines the storage format of the recorded file and the supported audio/video encoding types. For details about the formats, see [OH_AVRecorder_ContainerFormatType](capi-avrecorder-base-h.md#oh_avrecorder_containerformattype).|
| int32_t videoBitrate | Video encoding bit rate, in bit/s. For details about the value range, see [AVRecorderProfile](arkts-apis-media-i.md#avrecorderprofile9). A larger value indicates better video quality but a larger file size. A low bit rate is suitable for scenarios where network transmission or storage is limited, while a high bit rate is suitable for local high-quality storage. If the value is out of the valid range, the recording fails. The default value is **0**. This parameter is valid only during video recording.|
| [OH_AVRecorder_CodecMimeType](capi-avrecorder-base-h.md#oh_avrecorder_codecmimetype) videoCodec | MIME type of the video encoder. Different types of video encoders have different compression efficiency, image quality, and compatibility. For details about the encoder types, see [OH_AVRecorder_CodecMimeType](capi-avrecorder-base-h.md#oh_avrecorder_codecmimetype). When **isHdr** is set to **true**, the value of **videoCodec** must be **AVRECORDER_VIDEO_HEVC**. This parameter is valid only during video recording.|
| int32_t videoFrameWidth | Video frame width, in pixels. For details about the value range, see [AVRecorderProfile](arkts-apis-media-i.md#avrecorderprofile9). A larger value indicates higher video definition but a larger file size. The default value is **0**. If the value is **0**, video recording is not performed. If the value is out of the valid range, the recording fails.|
| int32_t videoFrameHeight | Video frame height, in pixels. For details about the value range, see [AVRecorderProfile](arkts-apis-media-i.md#avrecorderprofile9). A larger value indicates higher video definition but a larger file size. The default value is **0**. If the value is **0**, video recording is not performed. If the value is out of the valid range, the recording fails.|
| int32_t videoFrameRate | Video frame rate. A higher frame rate indicates smoother video playback but a larger file size. The unit is frames per second (FPS). For details about the value range, see [AVRecorderProfile](arkts-apis-media-i.md#avrecorderprofile9). If the value is beyond the valid range, the recording fails. The default value is **0**. This parameter is valid only during video recording.|
| bool isHdr | Whether HDR videos are recorded.<br> The value **true** indicates that HDR encoding is enabled. In this case, the value of **videoCodec** must be **AVRECORDER_VIDEO_HEVC**. Otherwise, the recording preparation fails. The value **false** indicates that HDR encoding is disabled, and there is no requirement on the encoding format.<br> The default value is **false**. This parameter is valid only during video recording.|
| bool enableTemporalScale | Whether to enable temporally scalable video encoding.<br> **true** indicates that some frames in the encoded output stream can be skipped to optimize encoding efficiency. This is applicable to scenarios where the encoding frame rate needs to be dynamically adjusted based on the network bandwidth or device performance (such as live video streaming and video conferencing). **false** indicates that all frames in the encoded output stream must be encoded without skipping. For details, see [Temporally Scalable Video Coding](../../media/avcodec/video-encoding-temporal-scalability.md).<br> The default value is **false**. This parameter is valid only during video recording.|
