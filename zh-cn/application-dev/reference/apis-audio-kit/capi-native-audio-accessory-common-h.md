# native_audio_accessory_common.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明外部音频配件设备接口的公共数据结构。

定义音频配件接口的公共类型。

**引用文件：** <ohaudio/native_audio_accessory_common.h>

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | 描述 |
| -- | -- |
| [OH_AudioAccessoryManager](#oh_audioaccessorymanager) | 声明音频配件管理器。 |
| [OH_AudioAccessory](#oh_audioaccessory) | 声明音频配件。 |
| [OH_AudioAccessoryInputStream](#oh_audioaccessoryinputstream) | 声明音频配件输入流。 |
| [OH_AudioAccessoryInfo](#oh_audioaccessoryinfo) | 定义音频配件的基本信息。 |
| [OH_AudioAccessoryNoiseReductionCapability](#oh_audioaccessorynoisereductioncapability) | 定义音频配件的降噪能力。 |
| [OH_AudioAccessoryCapabilities](#oh_audioaccessorycapabilities) | 定义音频配件的能力。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioAccessoryType](#oh_audioaccessorytype) | OH_AudioAccessoryType | 枚举音频配件连接类型。 |

## 枚举类型说明

### OH_AudioAccessoryType

```c
enum OH_AudioAccessoryType
```

**描述**

枚举音频配件连接类型。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_ACCESSORY_TYPE_BT_SPP = 1 | 蓝牙串行端口配置文件（Serial Port Profile，SPP）连接。 |

## 结构体说明

### OH_AudioAccessoryManager

```c
typedef struct OH_AudioAccessoryManager OH_AudioAccessoryManager
```

**描述**

声明音频配件管理器。

用于管理音频配件相关功能。

**起始版本：** 26.0.0

### OH_AudioAccessory

```c
typedef struct OH_AudioAccessory OH_AudioAccessory
```

**描述**

声明音频配件。

用于表示一个音频配件设备实例。

**起始版本：** 26.0.0

### OH_AudioAccessoryInputStream

```c
typedef struct OH_AudioAccessoryInputStream OH_AudioAccessoryInputStream
```

**描述**

声明音频配件输入流。

用于表示音频配件的输入音频流。

**起始版本：** 26.0.0

### OH_AudioAccessoryInfo

```c
typedef struct OH_AudioAccessoryInfo
```

**描述**

定义音频配件的基本信息。

**版本控制：** 调用方在将此结构体传递给框架之前，必须将structSize设置为sizeof(OH_AudioAccessoryInfo)。

**起始版本：** 26.0.0

| 成员变量 | 描述 |
| -- | -- |
| uint32_t structSize | 结构体大小，单位为字节（B）。<br>调用方必须初始化此字段（例如：info.structSize = sizeof(OH_AudioAccessoryInfo)）。<br>框架通过此字段判断所使用的结构体版本。 |
| const char *accessoryName | 配件名称，用于UX展示，如"DJI Mic 2"。<br>框架会对此字段进行深拷贝。 |
| const char *manufacturer | 制造商名称，如"DJI"。<br>框架会对此字段进行深拷贝。 |
| const char *modelNumber | 型号编号，如"CP236"。<br>框架会对此字段进行深拷贝。 |
| const char *macAddress | 配件MAC地址，如"00:11:22:33:44:55"。<br>框架会对此字段进行深拷贝。 |
| [OH_AudioAccessoryType](#oh_audioaccessorytype) type | 配件连接类型。 |
| bool isUnidirectional | 标识配件是否为单向音频设备。<br>true：单向设备；false：双向设备。 |

### OH_AudioAccessoryNoiseReductionCapability

```c
typedef struct OH_AudioAccessoryNoiseReductionCapability
```

**描述**

定义音频配件的降噪能力。

**起始版本：** 26.0.0

| 成员变量 | 描述 |
| -- | -- |
| uint32_t structSize | 结构体大小，单位为字节（B）。<br>调用方必须初始化此字段（例如：info.structSize = sizeof(OH_AudioAccessoryNoiseReductionCapability)）。<br>框架通过此字段判断所使用的结构体版本。 |
| const [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) *supportedModes | 支持的降噪模式数组。 |
| uint32_t supportedModeCount | 支持的降噪模式数量。 |
| [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) currentMode | 设备当前降噪模式。<br>表示注册能力时的初始状态。 |

### OH_AudioAccessoryCapabilities

```c
typedef struct OH_AudioAccessoryCapabilities
```

**描述**

定义音频配件的能力。

**版本控制：** 调用方必须将structSize设置为sizeof(OH_AudioAccessoryCapabilities)。

**起始版本：** 26.0.0

| 成员变量 | 描述 |
| -- | -- |
| uint32_t structSize | 结构体大小，单位为字节（B）。<br>调用方必须初始化此字段（例如：caps.structSize = sizeof(OH_AudioAccessoryCapabilities)）。 |
| const [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamProperties | 支持的音频流配置数组。<br>每个条目表示采样率、采样格式和声道数的有效组合。<br>框架会对此数组进行深拷贝。 |
| uint32_t streamPropertyCount | 支持的音频流配置数量。 |
