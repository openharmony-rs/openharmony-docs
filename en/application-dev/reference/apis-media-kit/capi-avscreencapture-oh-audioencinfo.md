# OH_AudioEncInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->

```c
typedef struct OH_AudioEncInfo {...} OH_AudioEncInfo
```

## Overview

Describes the audio encoding information.

This struct is used to configure the audio encoding parameters in the screen capture scenario, including the audio encoding bitrate and audio encoding format. By setting these parameters, you can control the audio quality and file size. This API is applicable to scenarios where the audio encoding quality and encoding mode need to be specified in the screen capture scenario. For details about the supported encoding formats, see [OH_AudioCodecFormat](capi-native-avscreen-capture-base-h.md#oh_audiocodecformat).

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t audioBitrate | Audio encoding bitrate, which is used to set the output bitrate of audio encoding. The value range depends on the bitrate range supported by the specific encoding format. Common values include **48000**, **96000**, and **128000**. The unit is bit/s. If the value is beyond the range supported by the encoding format, the encoding may fail.|
| [OH_AudioCodecFormat](capi-native-avscreen-capture-base-h.md#oh_audiocodecformat) audioCodecformat | Audio encoding format used during screen capture. Different encoding formats correspond to different encoding algorithms, compression efficiency, compatibility, and quality. The encoding format affects the size of the audio file, playback compatibility, and audio quality. For details about the supported encoding formats, see [OH_AudioCodecFormat](capi-native-avscreen-capture-base-h.md#oh_audiocodecformat).|
