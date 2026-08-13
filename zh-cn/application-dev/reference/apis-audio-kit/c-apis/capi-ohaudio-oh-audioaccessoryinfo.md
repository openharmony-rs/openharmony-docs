# OH_AudioAccessoryInfo

```c
typedef struct OH_AudioAccessoryInfo {...} OH_AudioAccessoryInfo
```

## 概述

定义音频配件的基本信息。<br><b>版本控制：</b>调用方在将此结构体传递给框架之前，必须将structSize设置为sizeof(OH_AudioAccessoryInfo)。

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t structSize | 结构体大小，单位为字节。<br> 调用方必须初始化此字段（例如：info.structSize = sizeof(OH_AudioAccessoryInfo)）。框架通过此字段判断所使用的结构体版本。<br>**起始版本：** 26.0.0 |
| const char *accessoryName | 配件名称，用于UX展示，如"DJI Mic 2"。<br> 框架会对此字段进行深拷贝。<br>**起始版本：** 26.0.0 |
| const char *manufacturer | 制造商名称，如"DJI"。<br> 框架会对此字段进行深拷贝。<br>**起始版本：** 26.0.0 |
| const char *modelNumber | 型号编号，如"CP236"。<br> 框架会对此字段进行深拷贝。<br>**起始版本：** 26.0.0 |
| const char *macAddress | 配件MAC地址，如"00:11:22:33:44:55"。<br> 框架会对此字段进行深拷贝。<br>**起始版本：** 26.0.0 |
| [OH_AudioAccessoryType](capi-native-audio-accessory-common-h.md#oh_audioaccessorytype) type | 配件连接类型。<br>**起始版本：** 26.0.0 |
| bool isUnidirectional | 标识配件是否为单向音频设备。<br> true：单向设备；false：双向设备。<br>**起始版本：** 26.0.0 |


