# OH_AudioAccessoryNoiseReductionCapability

```c
typedef struct OH_AudioAccessoryNoiseReductionCapability {...} OH_AudioAccessoryNoiseReductionCapability
```

## 概述

定义音频配件的降噪能力。

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t structSize | 此结构的大小（以字节为单位）。必须由调用者初始化（例如，info.structSize=sizeof(OH_AudioAccessoryNoiseReduceCapability）)。框架使用它来确定使用的是哪个版本的结构。<br>**起始版本：** 26.0.0 |
| const OH_AudioNoiseReductionMode *supportedModes | 支持的降噪模式数组。<br>**起始版本：** 26.0.0 |
| uint32_t supportedModeCount | 支持的降噪模式个数。<br>**起始版本：** 26.0.0 |
| OH_AudioNoiseReductionMode currentMode | 设备当前的降噪模式。这表示功能注册时的初始状态。<br>**起始版本：** 26.0.0 |


