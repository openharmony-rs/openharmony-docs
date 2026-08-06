# OH_AudioConverter_Format
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1961de06e85063963f633ec54a8a4baaf5cb7dc8 translatedAt=2026-07-21T03:49:57.996Z pushedAt=2026-07-21T07:09:45.047Z -->

```c
typedef struct OH_AudioConverter_Format {...} OH_AudioConverter_Format
```

## Overview

This struct defines the audio converter format data structure, which is used to describe the basic audio format.

**Since**: 26.0.0

**Related module**: AudioConverter](capi-audioconverter.md)

**Header file**: [native_audio_converter.h](capi-native-audio-converter-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_Audio_EncodingType](capi-native-audio-suite-base-h.md#oh_audio_encodingtype) encodingType | Audio encoding format type.<br>**Since**: 26.0.0|
| [OH_Audio_SampleRate](capi-native-audio-suite-base-h.md#oh_audio_samplerate) samplingRate | Audio sampling rate.<br>**Since**: 26.0.0|
| [OH_AudioChannelLayout](../../reference/apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | Audio channel layout.<br>**Since:** 26.0.0 |
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | Audio sample format.<br>**Since**: 26.0.0|