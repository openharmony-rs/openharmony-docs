# OH_AudioStreamInfo
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1ff9e9cd1ebb6561090ad32be99073f8301559bf translatedAt=2026-10-08T12:44:45.378Z pushedAt=2026-10-13T07:42:50.792Z -->

```c
typedef struct OH_AudioStreamInfo {...} OH_AudioStreamInfo
```

## Overview

Describes the audio stream information struct, which is used to describe the basic audio format.

**Since**: 19

**Related module**: [OHAudio](capi-ohaudio.md)

**Header file**: [native_audiostream_base.h](capi-native-audiostream-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t samplingRate | Sampling rate, in Hz. |
| [OH_AudioChannelLayout](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | Audio channel layout.|
| [OH_AudioStream_EncodingType](capi-native-audiostream-base-h.md#oh_audiostream_encodingtype) encodingType | Encoding type.|
| [OH_AudioStream_SampleFormat](capi-native-audiostream-base-h.md#oh_audiostream_sampleformat) sampleFormat | Sampling format.|


