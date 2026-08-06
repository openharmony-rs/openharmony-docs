# OH_AudioAccessoryInfo

```c
typedef struct OH_AudioAccessoryInfo {...} OH_AudioAccessoryInfo
```

## 概述

定义音频附件基本信息。<b>Version Control:</b>调用方必须将structSize设置为sizeof(OH_AudioAccessoryInfo)在将此结构传递给框架之前。

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t structSize | 此结构的大小（以字节为单位）。必须由调用者初始化（例如，info.structSize = sizeof(OH_AudioAccessoryInfo）)。框架使用它来确定使用的是哪个版本的结构。<br>**起始版本：** 26.0.0 |
| const char *accessoryName | UX显示的附件名称，如“DJI Mic 2”。框架会对该字段执行深拷贝。<br>**起始版本：** 26.0.0 |
| const char *manufacturer | 制造商名称，如“DJI”。框架会对该字段执行深拷贝。<br>**起始版本：** 26.0.0 |
| const char *modelNumber | 型号，如“CP236”。框架会对该字段执行深拷贝。<br>**起始版本：** 26.0.0 |
| const char *macAddress | 配件的MAC地址，如“00:11:22:33:44:55”。框架会对该字段执行深拷贝。<br>**起始版本：** 26.0.0 |
| [OH_AudioAccessoryType](capi-native-audio-accessory-common-h.md#oh_audioaccessorytype) type | 附件连接类型。<br>**起始版本：** 26.0.0 |
| bool isUnidirectional | 配件是否为单向音频设备。true：单向设备，false：双向设备。<br>**起始版本：** 26.0.0 |


