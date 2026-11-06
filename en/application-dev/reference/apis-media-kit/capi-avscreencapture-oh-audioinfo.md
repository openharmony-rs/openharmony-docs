# OH_AudioInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=73fcb44d9e98209c893b7750b907becdbdc9c224 translatedAt=2026-09-15T16:49:23.531Z pushedAt=2026-09-20T02:01:22.163Z -->

```c
typedef struct OH_AudioInfo {...} OH_AudioInfo
```

## Overview

Describes the audio information.

As an audio configuration item of **OH_ScreenCaptureConfig**, **OH_AudioInfo** contains the microphone capture information, internal recording capture information, and audio encoding information. You need to configure the microphone capture information or internal recording capture information based on the capture scenario, and configure the audio encoding information when encoding output is required. This struct is applicable to scenarios where audio data needs to be captured during screen capture.

When both the microphone audio and internal audio are captured, the values of **audioSampleRate** and **audioChannels** for the two audio streams must be the same. This is because the two audio streams will be combined into one audio stream for output. If the values are different, audio synchronization will be abnormal or the capture will fail.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_AudioCaptureInfo](capi-avscreencapture-oh-audiocaptureinfo.md) micCapInfo | Microphone audio capture information, which is used to configure the parameters for audio capture by the microphone. |
| [OH_AudioCaptureInfo](capi-avscreencapture-oh-audiocaptureinfo.md) innerCapInfo | Internal audio capture information, which is used to configure the parameters for internal audio capture. |
| [OH_AudioEncInfo](capi-avscreencapture-oh-audioencinfo.md) audioEncInfo | Audio encoding information. This parameter is not required during capture of the original stream. If this parameter is not set, audio encoding is not performed by default. |


