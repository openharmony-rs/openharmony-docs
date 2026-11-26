# OH_AudioSuite_ConverterOutputInfo
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AudioSuite_ConverterOutputInfo {...} OH_AudioSuite_ConverterOutputInfo
```

## 概述

定义用于接收音频转换结果的输出数据结构体。该结构体用于接收通过直接处理模式进行格式转换的音频数据。直接处理模式指通过直接传入输入数据（非回调模式）进行转换的处理方式。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

**所在头文件：** [native_audio_converter.h](capi-native-audio-converter-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| void *data | 输出音频数据缓冲区指针，由调用者分配。转换结果将写入此缓冲区。具体数据类型由采样格式[OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat)决定。调用[OH_AudioSuite_ConverterDirectProcess](capi-native-audio-converter-h.md#oh_audiosuite_converterdirectprocess)期间必须保持有效。不能为NULL。<br>**起始版本：** 26.1.0 |
| uint32_t size | 输出缓冲区容量，单位为字节（byte），必须大于0。<br>**起始版本：** 26.1.0 |
| uint32_t writeSize | 输出参数，返回实际写入输出缓冲区的字节数。调用前无需初始化；调用失败时不会写入内容。<br>**起始版本：** 26.1.0 |


