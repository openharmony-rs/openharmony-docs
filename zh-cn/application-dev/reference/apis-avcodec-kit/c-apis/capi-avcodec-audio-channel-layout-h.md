# avcodec_audio_channel_layout.h

## 概述

音频编解码声道布局枚举的声明。

**引用文件：** <multimedia/player_framework/avcodec_audio_channel_layout.h>

**库：** libnative_media_codecbase.so

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 10

**相关模块：** [CodecBase](capi-codecbase.md)

## 汇总

### 枚举

| 名称 | 描述 |
| -- | -- |
| [AudioChannelSet : uint64_t](#audiochannelset  uint64_t) | 音频声道数集合，将每一个声道数映射为uint64_t的变量。(API11废弃) |
| [AudioChannelLayout : uint64_t](#audiochannellayout  uint64_t) | 音频声道数类型，将用户申请的解码器输出格式表示为编解码器的声道类型。(API11废弃) |

## 枚举类型说明

### AudioChannelSet : uint64_t

```c
enum AudioChannelSet : uint64_t
```

**描述**

音频声道数集合，将每一个声道数映射为uint64_t的变量。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** OH_AudioChannelSet

| 枚举项 | 描述 |
| -- | -- |
|  | ACN（Ambisonic Channel Number立体声声道数）格式 |
|  | 零阶一阶立体声声道数 |
| AMBISONICS_ACN0 = 1ULL << 41U | 零阶立体声声道数0 |
| AMBISONICS_ACN1 = 1ULL << 42U | 一阶立体声声道数1 |
| AMBISONICS_ACN2 = 1ULL << 43U | 一阶立体声声道数2 |
| AMBISONICS_ACN3 = 1ULL << 44U | 一阶立体声声道数3 |
| AMBISONICS_W = AMBISONICS_ACN0 | 同于零阶立体声声道数0 |
| AMBISONICS_Y = AMBISONICS_ACN1 | 同于一阶立体声声道数1 |
| AMBISONICS_Z = AMBISONICS_ACN2 | 同于一阶立体声声道数2 |
| AMBISONICS_X = AMBISONICS_ACN3 | 同于一阶立体声声道数3 |
|  | 二阶立体声声道数 |
| AMBISONICS_ACN4 = 1ULL << 45U | 二阶立体声声道数4 |
| AMBISONICS_ACN5 = 1ULL << 46U | 二阶立体声声道数5 |
| AMBISONICS_ACN6 = 1ULL << 47U | 二阶立体声声道数6 |
| AMBISONICS_ACN7 = 1ULL << 48U | 二阶立体声声道数7 |
| AMBISONICS_ACN8 = 1ULL << 49U | 二阶立体声声道数8 |
|  | 三阶立体声声道数 |
| AMBISONICS_ACN9 = 1ULL << 50U | 三阶立体声声道数9 |
| AMBISONICS_ACN10 = 1ULL << 51U | 三阶立体声声道数10 |
| AMBISONICS_ACN11 = 1ULL << 52U | 三阶立体声声道数11 |
| AMBISONICS_ACN12 = 1ULL << 53U | 三阶立体声声道数12 |
| AMBISONICS_ACN13 = 1ULL << 54U | 三阶立体声声道数13 |
| AMBISONICS_ACN14 = 1ULL << 55U | 三阶立体声声道数14 |
| AMBISONICS_ACN15 = 1ULL << 56U | 三阶立体声声道数15 |

### AudioChannelLayout : uint64_t

```c
enum AudioChannelLayout : uint64_t
```

**描述**

音频声道数类型，将用户申请的解码器输出格式表示为编解码器的声道类型。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** OH_AudioChannelLayout

| 枚举项 | 描述 |
| -- | -- |


