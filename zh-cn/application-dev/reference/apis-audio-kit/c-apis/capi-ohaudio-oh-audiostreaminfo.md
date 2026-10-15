# OH_AudioStreamInfo

```c
struct OH_AudioStreamInfo {...}
```

## 概述

声明音频流信息结构体，该结构体用于表示音频基础格式，包括采样率、声道布局、编码格式和采样格式信息。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 19

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audiostream_base.h](capi-native-audiostream-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t samplingRate | 音频流采样率，单位为Hz。<br>**起始版本：** 19 |
| [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | 音频流声道布局。<br>**起始版本：** 19 |
| [OH_AudioStream_EncodingType](capi-native-audiostream-base-h.md#oh_audiostream_encodingtype) encodingType | 音频流编码格式。<br>**起始版本：** 19 |
| [OH_AudioStream_SampleFormat](capi-native-audiostream-base-h.md#oh_audiostream_sampleformat) sampleFormat | 音频流采样格式。<br>**起始版本：** 19 |


