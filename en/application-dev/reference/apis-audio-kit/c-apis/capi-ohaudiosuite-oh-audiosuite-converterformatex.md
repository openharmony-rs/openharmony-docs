# OH_AudioSuite_ConverterFormatEx

```c
struct OH_AudioSuite_ConverterFormatEx {...}
```

## Overview

Defines the format information of the extended audio converter, which is used to describe the audio format that supports any sampling rate.

<!--Device-struct OH_AudioSuite_ConverterFormatEx {...}--><!--Device-struct OH_AudioSuite_ConverterFormatEx {...}-End-->

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.1.0

**Related module**: [OHAudioSuite](capi-audio-kit-ohaudiosuite.md)

**Header file**: [native_audio_converter.h](capi-native-audio-converter-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_Audio_EncodingType](capi-native-audio-suite-base-h.md#oh_audio_encodingtype) encodingType | Audio encoding format type.<br>**Since**: 26.1.0 |
| int32_t samplingRate | Audio sampling rate, in Hz. The sampling rate is an integer multiple of 10 Hz in the range [8000, 5644800] and 11025 Hz.<br>**Since**: 26.1.0 |
| [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | Audio channel layout. The supported value range is [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_MONO, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_STEREO, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_STEREO_DOWNMIX, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_2POINT1, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_3POINT0, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_SURROUND, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_3POINT1, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_4POINT0, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_QUAD_SIDE, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_QUAD, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_2POINT0POINT2, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_4POINT1, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT0, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT0_BACK, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_2POINT1POINT2, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_3POINT0POINT2, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT1, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT1_BACK, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_6POINT0, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_3POINT1POINT2, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_6POINT0_FRONT, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_HEXAGONAL, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_6POINT1, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_6POINT1_BACK, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_6POINT1_FRONT, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT0, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT0_FRONT, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT1, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_OCTAGONAL, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT1POINT2, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT1_WIDE, [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT1_WIDE_BACK.<br>**Since**: 26.1.0 |
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | Audio sampling format.<br>**Since**: 26.1.0 |


