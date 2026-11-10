# OH_AudioSuite_ConverterFormatEx

```c
struct OH_AudioSuite_ConverterFormatEx {...}
```

## 概述

定义扩展音频转换器格式信息结构体，用于描述支持任意采样率的音频格式。

<!--Device-struct OH_AudioSuite_ConverterFormatEx {...}--><!--Device-struct OH_AudioSuite_ConverterFormatEx {...}-End-->

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.1.0

**相关模块：** [OHAudioSuite](capi-audio-kit-ohaudiosuite.md)

**所在头文件：** [native_audio_converter.h](capi-native-audio-converter-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_Audio_EncodingType](capi-native-audio-suite-base-h.md#oh_audio_encodingtype) encodingType | 音频编码格式类型。<br>**起始版本：** 26.1.0 |
| int32_t samplingRate | 音频采样率，单位为赫兹（Hz）。 支持[8000, 5644800]范围内10Hz整数倍的采样率，以及11025Hz。<br>**起始版本：** 26.1.0 |
| [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | 音频声道布局。 支持的取值范围为[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_MONO、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_STEREO、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_STEREO_DOWNMIX、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_2POINT1、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_3POINT0、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_SURROUND、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_3POINT1、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_4POINT0、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_QUAD_SIDE、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_QUAD、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_2POINT0POINT2、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_4POINT1、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT0、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT0_BACK、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_2POINT1POINT2、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_3POINT0POINT2、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT1、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT1_BACK、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_6POINT0、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_3POINT1POINT2、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_6POINT0_FRONT、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_HEXAGONAL、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_6POINT1、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_6POINT1_BACK、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_6POINT1_FRONT、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT0、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT0_FRONT、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT1、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_OCTAGONAL、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_5POINT1POINT2、[OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT1_WIDE、 [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout).CH_LAYOUT_7POINT1_WIDE_BACK。<br>**起始版本：** 26.1.0 |
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | 音频采样格式。<br>**起始版本：** 26.1.0 |


