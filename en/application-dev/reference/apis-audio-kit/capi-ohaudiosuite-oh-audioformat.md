# OH_AudioFormat
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=e9ec8701c87cf0327fd7aa17be40e1c4aeed0156 translatedAt=2026-11-09T10:26:57.394Z pushedAt=2026-11-09T11:30:42.152Z nl=1 -->

```c
typedef struct OH_AudioFormat {...} OH_AudioFormat
```

## Overview

The struct describes the audio stream information, which is used to describe the basic audio format, required for audio creation.

**Since**: 22

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_Audio_SampleRate](capi-native-audio-suite-base-h.md#oh_audio_samplerate) samplingRate | Sample rate of the audio stream.|
| [OH_AudioChannelLayout](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | Audio channel layout.<br>Before API version 26.0.0, only CH_LAYOUT_MONO and CH_LAYOUT_STEREO are supported.<br>From API version 26.0.0 onward, CH_LAYOUT_MONO, CH_LAYOUT_STEREO, CH_LAYOUT_STEREO_DOWNMIX, CH_LAYOUT_2POINT1, CH_LAYOUT_3POINT0, CH_LAYOUT_SURROUND, CH_LAYOUT_3POINT1, CH_LAYOUT_4POINT0, CH_LAYOUT_QUAD_SIDE, CH_LAYOUT_QUAD, CH_LAYOUT_2POINT0POINT2, CH_LAYOUT_4POINT1, CH_LAYOUT_5POINT0, CH_LAYOUT_5POINT0_BACK, CH_LAYOUT_2POINT1POINT2, CH_LAYOUT_3POINT0POINT2, CH_LAYOUT_5POINT1, CH_LAYOUT_5POINT1_BACK, CH_LAYOUT_6POINT0, CH_LAYOUT_3POINT1POINT2, CH_LAYOUT_6POINT0_FRONT, CH_LAYOUT_HEXAGONAL, CH_LAYOUT_6POINT1, CH_LAYOUT_6POINT1_BACK, CH_LAYOUT_6POINT1_FRONT, CH_LAYOUT_7POINT0, CH_LAYOUT_7POINT0_FRONT, CH_LAYOUT_7POINT1, CH_LAYOUT_OCTAGONAL, CH_LAYOUT_5POINT1POINT2, CH_LAYOUT_7POINT1_WIDE, CH_LAYOUT_7POINT1_WIDE_BACK, CH_LAYOUT_AMB_ORDER1_ACN_N3D, CH_LAYOUT_AMB_ORDER1_ACN_SN3D, CH_LAYOUT_AMB_ORDER1_FUMA, CH_LAYOUT_AMB_ORDER2_ACN_N3D, CH_LAYOUT_AMB_ORDER2_ACN_SN3D, CH_LAYOUT_AMB_ORDER2_FUMA, CH_LAYOUT_AMB_ORDER3_ACN_N3D, CH_LAYOUT_AMB_ORDER3_ACN_SN3D, and CH_LAYOUT_AMB_ORDER3_FUMA are supported. |
| uint32_t channelCount | Number of audio channels.<br>Before API version 26.0.0, only 1 channel and 2 channels are supported.<br>From API version 26.0.0 onward, 1 to 9 channels and 16 channels are supported. |
| [OH_Audio_EncodingType](capi-native-audio-suite-base-h.md#oh_audio_encodingtype) encodingType | Encoding type used for the audio stream.|
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | Sample format of the audio stream.|


