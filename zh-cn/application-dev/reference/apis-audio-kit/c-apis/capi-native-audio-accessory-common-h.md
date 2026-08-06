# native_audio_accessory_common.h

## 概述

Declare common types for external audio accessory device interfaces.

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioAccessoryInfo](capi-ohaudio-oh-audioaccessoryinfo.md) | OH_AudioAccessoryInfo | 定义音频附件基本信息。<b>Version Control:</b>调用方必须将structSize设置为sizeof(OH_AudioAccessoryInfo)在将此结构传递给框架之前。 |
| [OH_AudioAccessoryNoiseReductionCapability](capi-ohaudio-oh-audioaccessorynoisereductioncapability.md) | OH_AudioAccessoryNoiseReductionCapability | 定义音频配件的降噪能力。 |
| [OH_AudioAccessoryCapabilities](capi-ohaudio-oh-audioaccessorycapabilities.md) | OH_AudioAccessoryCapabilities | 定义音频配件的能力。<b>Version Control:</b>调用方必须将structSize设置为sizeof(OH_AudioAccessoryCapability)。 |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) | OH_AudioAccessoryManager | 声明音频附件管理器。 |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) | OH_AudioAccessory | 声明音频附件。 |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) | OH_AudioAccessoryInputStream | 声明音频附件输入流。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioAccessoryType](#oh_audioaccessorytype) | OH_AudioAccessoryType | 枚举音频附件连接类型。 |

## 枚举类型说明

### OH_AudioAccessoryType

```c
enum OH_AudioAccessoryType
```

**描述**

枚举音频附件连接类型。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| * @since 26.0.0 |  |
| AUDIO_ACCESSORY_TYPE_BT_SPP = 1 | 蓝牙SPP（信号处理插件）连接。 *<br>**起始版本：** 26.0.0 |


