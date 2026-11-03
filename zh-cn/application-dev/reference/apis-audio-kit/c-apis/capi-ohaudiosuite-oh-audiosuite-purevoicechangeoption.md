# OH_AudioSuite_PureVoiceChangeOption

```c
struct OH_AudioSuite_PureVoiceChangeOption {...}
```

## 概述

定义音频编创传统变声选项。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 23

**相关模块：** [OHAudioSuite](capi-others-ohaudiosuite.md)

**所在头文件：** [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_AudioSuite_PureVoiceChangeGenderOption](capi-native-audio-suite-base-h.md#oh_audiosuite_purevoicechangegenderoption) optionGender | 指定传统变声性别。<br>**起始版本：** 23 |
| [OH_AudioSuite_PureVoiceChangeType](capi-native-audio-suite-base-h.md#oh_audiosuite_purevoicechangetype) optionType | 指定传统变声类型。<br>**起始版本：** 23 |
| float pitch | 指定传统变声音调。如果使用系统中的默认音调以获得最佳效果，设置为宏定义中的OH_PURE_VOICE_DEFAULT_PITCH。 <br> 设置自定义音调的取值范围为[0.3f, 3.0f]。<br>**起始版本：** 23 |


