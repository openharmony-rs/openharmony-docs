# OH_AudioFormat
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_AudioFormat
```

## 概述

定义音频编创的音频流信息，用于描述基本音频格式。

**起始版本：** 22

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

**所在头文件：** [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_Audio_SampleRate](capi-native-audio-suite-base-h.md#oh_audio_samplerate) samplingRate | 音频流采样率。 |
| [OH_AudioChannelLayout](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | 音频流声道布局，在API version 26.0.0之前，仅支持[CH_LAYOUT_MONO](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) 和 [CH_LAYOUT_STEREO](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)；在API version 26.0.0及以后，支持[CH_LAYOUT_MONO](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_STEREO](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_STEREO_DOWNMIX](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_2POINT1](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_3POINT0](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_SURROUND](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_3POINT1](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_4POINT0](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_QUAD_SIDE](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_QUAD](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_2POINT0POINT2](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_4POINT1](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_5POINT0](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_5POINT0_BACK](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_2POINT1POINT2](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_3POINT0POINT2](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_5POINT1](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_5POINT1_BACK](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_6POINT0](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_3POINT1POINT2](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_6POINT0_FRONT](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_HEXAGONAL](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_6POINT1](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_6POINT1_BACK](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_6POINT1_FRONT](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_7POINT0](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_7POINT0_FRONT](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_7POINT1](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_OCTAGONAL](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_5POINT1POINT2](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_7POINT1_WIDE](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)、[CH_LAYOUT_7POINT1_WIDE_BACK](../apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)。 |
| uint32_t channelCount | 音频流声道数。<br>在API版本26.0.0之前，仅支持1声道和2声道；在API版本26.0.0及以后，支持1至8声道。 |
| [OH_Audio_EncodingType](capi-native-audio-suite-base-h.md#oh_audio_encodingtype) encodingType | 音频流编码类型。 |
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | 音频流采样格式。 |


