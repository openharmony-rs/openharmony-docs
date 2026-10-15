# OH_AudioDeviceDescriptorArray

```c
struct OH_AudioDeviceDescriptorArray {...}
```

## 概述

声明音频设备描述符数组的结构体，该结构体表示一组音频设备描述符，通过每个描述符可查询设备详细信息。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audio_device_base.h](capi-native-audio-device-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t size | 音频设备描述符数组元素个数。 |
| OH_AudioDeviceDescriptor **descriptors | 指向音频设备描述符数组的指针。 |


