# OH_EqualizerFrequencyBandGains

```c
struct OH_EqualizerFrequencyBandGains {...}
```

## 概述

定义音频编创均衡器效果节点配置参数。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 22

**相关模块：** [OHAudioSuite](capi-others-ohaudiosuite.md)

**所在头文件：** [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t gains[EQUALIZER_BAND_NUM] | 均衡器频带增益配置。数组长度为10，增益输入范围为[-10, 10]，单位为dB（分贝）。 频带：31Hz、62Hz、125Hz、250Hz、500Hz、1kHz、2kHz、4kHz、8kHz、16kHz。<br>**起始版本：** 22 |


