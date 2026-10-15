# OH_AudioSuite_SystemNodeFormat（系统接口）

```c
struct OH_AudioSuite_SystemNodeFormat {...}
```

## 概述

定义系统节点的基本音频格式。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

**所在头文件：** [native_audio_suite_base.h（系统接口）](capi-native-audio-suite-base-h-sys.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_Audio_SampleRate](capi-native-audio-suite-base-h.md#oh_audio_samplerate) samplingRate | 音频流采样率。<br>**起始版本：** 26.0.0 |
| [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | 音频流声道布局。<br>**起始版本：** 26.0.0 |
| uint32_t channelCount | 音频流声道个数。<br>**起始版本：** 26.0.0 |
| int32_t encoding | 音频流编码类型。取值为1或者9，1表示PCM编码格式，9表示PCM与MetaData混合音频数据。<br>**起始版本：** 26.0.0 |
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | 音频流采样格式。<br>**起始版本：** 26.0.0 |


