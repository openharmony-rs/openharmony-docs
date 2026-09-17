# native_audio_suite_base.h（系统接口）

## 概述

声明音频编创相关底层数据结构。

**库：** libohaudiosuite.so

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 22

**系统接口：** 此接口为系统接口。

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioSuite_SystemNodeFormat（系统接口）](capi-ohaudiosuite-oh-audiosuite-systemnodeformat-sys.md) | OH_AudioSuite_SystemNodeFormat | 定义音频格式信息结构，用于描述系统节点的基本音频格式。**系统接口：** 此接口为系统接口。 |
| [OH_AudioSuite_MetaFrame（系统接口）](capi-ohaudiosuite-oh-audiosuite-metaframe-sys.md) | OH_AudioSuite_MetaFrame | 定义音频元数据帧结构。 该结构用于将音频数据和元数据一起传递。**系统接口：** 此接口为系统接口。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioSuite_SystemNodeType（系统接口）](#oh_audiosuite_systemnodetype) | OH_AudioSuite_SystemNodeType | 定义音频节点系统类型。**系统接口：** 此接口为系统接口。 |

## 枚举类型说明

### OH_AudioSuite_SystemNodeType

```c
enum OH_AudioSuite_SystemNodeType
```

**描述：**

定义音频节点系统类型。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

| 枚举项 | 描述 |
| -- | -- |
| OH_AUDIOSUITE_EFFECT_NODE_SYSTEM_TYPE_DIALOGUE_ENHANCE = 301 |  |
| OH_AUDIOSUITE_EFFECT_NODE_SYSTEM_TYPE_VOICE_BEAUTIFIER = 302 |  |


