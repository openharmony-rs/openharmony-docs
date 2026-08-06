# OH_AudioAccessoryCapabilities

```c
typedef struct OH_AudioAccessoryCapabilities {...} OH_AudioAccessoryCapabilities
```

## 概述

定义音频配件的能力。<b>Version Control:</b>调用方必须将structSize设置为sizeof(OH_AudioAccessoryCapability)。

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t structSize | 此结构的大小（以字节为单位）。必须由调用者初始化（例如，caps.structSize=sizeof(OH_AudioAccessoryCapability）)。<br>**起始版本：** 26.0.0 |
| const [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamProperties | 支持的流配置数组。每个条目代表一个有效的采样速率组合，格式和通道数。框架执行此数组的深拷贝。<br>**起始版本：** 26.0.0 |
| uint32_t streamPropertyCount | 支持的码流配置个数。<br>**起始版本：** 26.0.0 |


