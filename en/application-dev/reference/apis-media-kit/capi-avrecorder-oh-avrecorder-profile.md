# OH_AVRecorder_Profile
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @shiwei75-->
<!--Designer: @HmQQQ-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

## Overview

The struct describes the parameters used for audio and video recording.

You can choose to record only audio or only video by setting the parameters.

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
| int32_t audioBitrate | Audio bit rate.|
| int32_t audioChannels | Number of channels.|
| [OH_AVRecorder_CodecMimeType](capi-avrecorder-base-h.md#oh_avrecorder_codecmimetype) audioCodec | Audio encoding format.|
| int32_t audioSampleRate | Audio sample rate.|
| [OH_AVRecorder_ContainerFormatType](capi-avrecorder-base-h.md#oh_avrecorder_containerformattype) fileFormat | Output file format.|
| int32_t videoBitrate | Video bit rate.|
| [OH_AVRecorder_CodecMimeType](capi-avrecorder-base-h.md#oh_avrecorder_codecmimetype) videoCodec | Video encoding format.|
| int32_t videoFrameWidth | Video width.|
| int32_t videoFrameHeight | Video height.|
| int32_t videoFrameRate | Video frame rate.|
| bool isHdr | Whether HDR videos are recorded.<br> **true** if recorded, **false** otherwise.<br> The default value is **false**.|
| bool enableTemporalScale | Whether temporal scalable encoding is enabled.<br> When this parameter is set to **true**, some frames in the encoded output stream can be skipped to optimize encoding efficiency. When it is set to **false**, all frames in the encoded output stream must be encoded without skipping. For details, see [Temporally Scalable Video Coding](../../media/avcodec/video-encoding-temporal-scalability.md)<br> The default value is **false**.|
