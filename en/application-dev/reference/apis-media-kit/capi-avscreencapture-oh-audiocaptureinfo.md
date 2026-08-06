# OH_AudioCaptureInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4b1a2f751fcd33c52248528ed8c23a9b2935126b translatedAt=2026-06-23T01:05:35.092Z pushedAt=2026-06-23T06:12:23.691Z -->

```c
typedef struct OH_AudioCaptureInfo {...} OH_AudioCaptureInfo
```

## Overview

The struct describes the audio capture information.

When both **audioSampleRate** and **audioChannels** are **0**, the audio-related parameters are ignored and the audio data is not recorded.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t audioSampleRate | Audio sampling rate. For the supported list, refer to [AudioSamplingRate](../apis-audio-kit/arkts-apis-audio-e.md#audiosamplingrate8) in Audio Kit. The unit is hertz (Hz). |
| int32_t audioChannels | Audio channel count.|
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) audioSource | Audio source.|