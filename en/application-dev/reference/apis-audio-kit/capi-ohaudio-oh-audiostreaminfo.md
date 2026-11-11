# OH_AudioStreamInfo
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=b8179ddefd55f69157fab19cdf0a8474af82997d translatedAt=2026-11-03T04:22:46.199Z pushedAt=2026-11-04T03:11:47.013Z nl=1 -->

```c
typedef struct OH_AudioStreamInfo {...} OH_AudioStreamInfo
```

## Overview

Defines the audio stream information struct, which is used to describe the basic audio format.

**Since**: 19

**Related module**: [OHAudio](capi-ohaudio.md)

**Header file**: [native_audiostream_base.h](capi-native-audiostream-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t samplingRate | Audio stream sampling rate. The unit is hertz (Hz). |
| [OH_AudioChannelLayout](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | Audio channel layout.|
| [OH_AudioStream_EncodingType](capi-native-audiostream-base-h.md#oh_audiostream_encodingtype) encodingType | Encoding type.|
| [OH_AudioStream_SampleFormat](capi-native-audiostream-base-h.md#oh_audiostream_sampleformat) sampleFormat | Sampling format.|


