# OH_AudioAccessoryNoiseReductionCapability

```c
typedef struct OH_AudioAccessoryNoiseReductionCapability {...} OH_AudioAccessoryNoiseReductionCapability
```

## 概述

定义音频配件的降噪能力。<br>

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t structSize | 结构体大小，单位为字节。<br> 调用方必须初始化此字段（例如：info.structSize = sizeof(OH_AudioAccessoryNoiseReductionCapability)）。框架通过此字段判断所使用的结构体版本。<br>**起始版本：** 26.0.0 |
| const [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) *supportedModes | 支持的降噪模式数组。<br>**起始版本：** 26.0.0 |
| uint32_t supportedModeCount | 支持的降噪模式数量。<br>**起始版本：** 26.0.0 |
| [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) currentMode | 设备当前降噪模式。<br> 表示注册能力时的初始状态。<br>**起始版本：** 26.0.0 |


