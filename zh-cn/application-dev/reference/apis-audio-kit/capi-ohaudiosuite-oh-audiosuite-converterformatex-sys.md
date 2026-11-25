# OH_AudioSuite_ConverterFormatEx
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AudioSuite_ConverterFormatEx {...} OH_AudioSuite_ConverterFormatEx
```

## 概述

定义扩展音频转换器的格式信息结构体，用于描述支持任意采样率的音频格式。采样率须为10Hz的整数倍并且在`[8000Hz, 5644800Hz]`范围内；11025Hz不受该限制。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

**所在头文件：** [native_audio_converter.h](capi-native-audio-converter-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_Audio_EncodingType](capi-native-audio-suite-base-h.md#oh_audio_encodingtype) encodingType | 音频编码格式。取值为 OH_Audio_EncodingType中的枚举值<br>**起始版本：** 26.1.0 |
| int32_t samplingRate | 音频采样率，单位为赫兹（Hz）。支持`[8000, 5644800]`Hz范围内10Hz整数倍的采样率，以及11025Hz。<br>**起始版本：** 26.1.0 |
| [OH_AudioChannelLayout](../../reference/apis-avcodec-kit/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | 音频声道布局，取值范围如下：<ul><li>1声道：`CH_LAYOUT_MONO`</li><li>2声道：`CH_LAYOUT_STEREO`、`CH_LAYOUT_STEREO_DOWNMIX`</li><li>3声道：`CH_LAYOUT_2POINT1`、`CH_LAYOUT_3POINT0`、`CH_LAYOUT_SURROUND`</li><li>4声道：`CH_LAYOUT_3POINT1`、`CH_LAYOUT_4POINT0`、`CH_LAYOUT_QUAD`、`CH_LAYOUT_QUAD_SIDE`、`CH_LAYOUT_2POINT0POINT2`</li><li>5声道：`CH_LAYOUT_4POINT1`、`CH_LAYOUT_5POINT0`、`CH_LAYOUT_5POINT0_BACK`、`CH_LAYOUT_2POINT1POINT2`、`CH_LAYOUT_3POINT0POINT2`</li><li>6声道：`CH_LAYOUT_5POINT1`、`CH_LAYOUT_5POINT1_BACK`、`CH_LAYOUT_6POINT0`、`CH_LAYOUT_3POINT1POINT2`、`CH_LAYOUT_6POINT0_FRONT`、`CH_LAYOUT_HEXAGONAL`</li><li>7声道：`CH_LAYOUT_6POINT1`、`CH_LAYOUT_6POINT1_BACK`、`CH_LAYOUT_6POINT1_FRONT`、`CH_LAYOUT_7POINT0`、`CH_LAYOUT_7POINT0_FRONT`</li><li>8声道：`CH_LAYOUT_7POINT1`、`CH_LAYOUT_OCTAGONAL`、`CH_LAYOUT_5POINT1POINT2`、`CH_LAYOUT_7POINT1_WIDE`、`CH_LAYOUT_7POINT1_WIDE_BACK`</li></ul>**起始版本：** 26.1.0 |
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | 音频采样格式。<br>**起始版本：** 26.1.0 |

