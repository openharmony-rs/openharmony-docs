# OH_AudioSuite_ConverterInputInfo
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AudioSuite_ConverterInputInfo {...} OH_AudioSuite_ConverterInputInfo
```

## 概述

定义音频转换器输入数据结构体。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

**所在头文件：** [native_audio_converter.h](capi-native-audio-converter-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const void *data | 输入音频数据缓冲区指针，指向音频原始数据，由调用者分配，具体数据类型由采样格式[OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat)决定。调用[OH_AudioSuite_ConverterDirectProcess](capi-native-audio-converter-h.md#oh_audiosuite_converterdirectprocess)期间必须保持有效。不能为NULL。<br>**起始版本：** 26.1.0 |
| uint32_t size | 输入音频数据字节数，即本次传入的有效数据长度。必须大于0，且必须是最小输入字节数的整数倍。<br>**起始版本：** 26.1.0 |


