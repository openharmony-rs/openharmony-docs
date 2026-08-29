# OH_AudioSuite_SystemNodeFormat

```c
typedef struct OH_AudioSuite_SystemNodeFormat {...} OH_AudioSuite_SystemNodeFormat
```

## 概述

定义音频格式信息结构，用于描述系统节点的基本音频格式。

**起始版本：** 26.0.0

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

**所在头文件：** [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_Audio_SampleRate](capi-native-audio-suite-base-h.md#oh_audio_samplerate) samplingRate | 音频采样率。<br>**起始版本：** 26.0.0 |
| OH_AudioChannelLayout channelLayout | 声道布局。<br>**起始版本：** 26.0.0 |
| uint32_t channelCount | 音频通道数。<br>**起始版本：** 26.0.0 |
| int32_t encoding | 音频编码格式。<br>**起始版本：** 26.0.0 |
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | 音频样本格式。<br>**起始版本：** 26.0.0 |


