# OH_AudioCaptureInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->

```c
typedef struct OH_AudioCaptureInfo {...} OH_AudioCaptureInfo
```

## Overview

Describes the audio capture information.

This struct is used to configure the audio capture parameters in screen capture, including the sampling rate, number of audio channels, and audio source type. You can set the **audioSampleRate** and **audioChannels** parameters to control the quality and channel layout of the recorded audio. This API is applicable to scenarios where the system audio or microphone audio needs to be captured during screen capture.

When both **audioSampleRate** and **audioChannels** are **0**, the audio-related parameters are ignored and the audio data is not recorded.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t audioSampleRate | Audio sample rate. For details about the supported rates, see [AudioSamplingRate](../apis-audio-kit/arkts-apis-audio-e.md#audiosamplingrate8) of Audio Kit. The unit is Hz. When both **audioSampleRate** and **audioChannels** are **0**, the audio-related parameters are ignored.|
| int32_t audioChannels | Number of audio channels. For details about the supported range, see [AudioChannel](../apis-audio-kit/arkts-apis-audio-e.md#audiochannel8). When both **audioSampleRate** and **audioChannels** are **0**, the audio-related parameters are ignored.|
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) audioSource | Audio source, such as the system audio or microphone recording. For details about the options, see [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype).|
