# avcodec_audio_channel_layout.h

## 概述

音频编解码声道布局枚举的声明。

**引用文件：** <multimedia/player_framework/avcodec_audio_channel_layout.h>

**库：** libnative_media_codecbase.so

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 10

**相关模块：** [CodecBase](capi-avcodec-kit-codecbase.md)

## 汇总

### 枚举

| 名称 | 描述 |
| -- | -- |
| [AudioChannelSet](#audiochannelset) | 音频声道数集合，将每一个声道数映射为uint64_t的变量。(已废弃) |
| [AudioChannelLayout](#audiochannellayout) | 音频声道数类型，将用户申请的解码器输出格式表示为编解码器的声道类型。(已废弃) |

## 枚举类型说明

### AudioChannelSet

```c
enum AudioChannelSet : uint64_t
```

**描述：**

音频声道数集合，将每一个声道数映射为uint64_t的变量。

<!--Device-enum AudioChannelSet : uint64_t--><!--Device-enum AudioChannelSet : uint64_t-End-->

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 10

**废弃版本：** 11

**替代接口：** OH_AudioChannelSet

| 枚举项 | 描述 |
| -- | -- |
| FRONT_LEFT = 1ULL << 0U | <!--Device-FRONT_LEFT = 1ULL << 0U--><!--Device-FRONT_LEFT = 1ULL << 0U-End--> |
| FRONT_RIGHT = 1ULL << 1U | <!--Device-FRONT_RIGHT = 1ULL << 1U--><!--Device-FRONT_RIGHT = 1ULL << 1U-End--> |
| FRONT_CENTER = 1ULL << 2U | <!--Device-FRONT_CENTER = 1ULL << 2U--><!--Device-FRONT_CENTER = 1ULL << 2U-End--> |
| LOW_FREQUENCY = 1ULL << 3U | <!--Device-LOW_FREQUENCY = 1ULL << 3U--><!--Device-LOW_FREQUENCY = 1ULL << 3U-End--> |
| BACK_LEFT = 1ULL << 4U | <!--Device-BACK_LEFT = 1ULL << 4U--><!--Device-BACK_LEFT = 1ULL << 4U-End--> |
| BACK_RIGHT = 1ULL << 5U | <!--Device-BACK_RIGHT = 1ULL << 5U--><!--Device-BACK_RIGHT = 1ULL << 5U-End--> |
| FRONT_LEFT_OF_CENTER = 1ULL << 6U | <!--Device-FRONT_LEFT_OF_CENTER = 1ULL << 6U--><!--Device-FRONT_LEFT_OF_CENTER = 1ULL << 6U-End--> |
| FRONT_RIGHT_OF_CENTER = 1ULL << 7U | <!--Device-FRONT_RIGHT_OF_CENTER = 1ULL << 7U--><!--Device-FRONT_RIGHT_OF_CENTER = 1ULL << 7U-End--> |
| BACK_CENTER = 1ULL << 8U | <!--Device-BACK_CENTER = 1ULL << 8U--><!--Device-BACK_CENTER = 1ULL << 8U-End--> |
| SIDE_LEFT = 1ULL << 9U | <!--Device-SIDE_LEFT = 1ULL << 9U--><!--Device-SIDE_LEFT = 1ULL << 9U-End--> |
| SIDE_RIGHT = 1ULL << 10U | <!--Device-SIDE_RIGHT = 1ULL << 10U--><!--Device-SIDE_RIGHT = 1ULL << 10U-End--> |
| TOP_CENTER = 1ULL << 11U | <!--Device-TOP_CENTER = 1ULL << 11U--><!--Device-TOP_CENTER = 1ULL << 11U-End--> |
| TOP_FRONT_LEFT = 1ULL << 12U | <!--Device-TOP_FRONT_LEFT = 1ULL << 12U--><!--Device-TOP_FRONT_LEFT = 1ULL << 12U-End--> |
| TOP_FRONT_CENTER = 1ULL << 13U | <!--Device-TOP_FRONT_CENTER = 1ULL << 13U--><!--Device-TOP_FRONT_CENTER = 1ULL << 13U-End--> |
| TOP_FRONT_RIGHT = 1ULL << 14U | <!--Device-TOP_FRONT_RIGHT = 1ULL << 14U--><!--Device-TOP_FRONT_RIGHT = 1ULL << 14U-End--> |
| TOP_BACK_LEFT = 1ULL << 15U | <!--Device-TOP_BACK_LEFT = 1ULL << 15U--><!--Device-TOP_BACK_LEFT = 1ULL << 15U-End--> |
| TOP_BACK_CENTER = 1ULL << 16U | <!--Device-TOP_BACK_CENTER = 1ULL << 16U--><!--Device-TOP_BACK_CENTER = 1ULL << 16U-End--> |
| TOP_BACK_RIGHT = 1ULL << 17U | <!--Device-TOP_BACK_RIGHT = 1ULL << 17U--><!--Device-TOP_BACK_RIGHT = 1ULL << 17U-End--> |
| STEREO_LEFT = 1ULL << 29U | <!--Device-STEREO_LEFT = 1ULL << 29U--><!--Device-STEREO_LEFT = 1ULL << 29U-End--> |
| STEREO_RIGHT = 1ULL << 30U | <!--Device-STEREO_RIGHT = 1ULL << 30U--><!--Device-STEREO_RIGHT = 1ULL << 30U-End--> |
| WIDE_LEFT = 1ULL << 31U | <!--Device-WIDE_LEFT = 1ULL << 31U--><!--Device-WIDE_LEFT = 1ULL << 31U-End--> |
| WIDE_RIGHT = 1ULL << 32U | <!--Device-WIDE_RIGHT = 1ULL << 32U--><!--Device-WIDE_RIGHT = 1ULL << 32U-End--> |
| SURROUND_DIRECT_LEFT = 1ULL << 33U | <!--Device-SURROUND_DIRECT_LEFT = 1ULL << 33U--><!--Device-SURROUND_DIRECT_LEFT = 1ULL << 33U-End--> |
| SURROUND_DIRECT_RIGHT = 1ULL << 34U | <!--Device-SURROUND_DIRECT_RIGHT = 1ULL << 34U--><!--Device-SURROUND_DIRECT_RIGHT = 1ULL << 34U-End--> |
| LOW_FREQUENCY_2 = 1ULL << 35U | <!--Device-LOW_FREQUENCY_2 = 1ULL << 35U--><!--Device-LOW_FREQUENCY_2 = 1ULL << 35U-End--> |
| TOP_SIDE_LEFT = 1ULL << 36U | <!--Device-TOP_SIDE_LEFT = 1ULL << 36U--><!--Device-TOP_SIDE_LEFT = 1ULL << 36U-End--> |
| TOP_SIDE_RIGHT = 1ULL << 37U | <!--Device-TOP_SIDE_RIGHT = 1ULL << 37U--><!--Device-TOP_SIDE_RIGHT = 1ULL << 37U-End--> |
| BOTTOM_FRONT_CENTER = 1ULL << 38U | <!--Device-BOTTOM_FRONT_CENTER = 1ULL << 38U--><!--Device-BOTTOM_FRONT_CENTER = 1ULL << 38U-End--> |
| BOTTOM_FRONT_LEFT = 1ULL << 39U | <!--Device-BOTTOM_FRONT_LEFT = 1ULL << 39U--><!--Device-BOTTOM_FRONT_LEFT = 1ULL << 39U-End--> |
| BOTTOM_FRONT_RIGHT = 1ULL << 40U | <!--Device-BOTTOM_FRONT_RIGHT = 1ULL << 40U--><!--Device-BOTTOM_FRONT_RIGHT = 1ULL << 40U-End--> |
| AMBISONICS_ACN0 = 1ULL << 41U | 零阶立体声声道数0<br><!--Device-AMBISONICS_ACN0 = 1ULL << 41U--><!--Device-AMBISONICS_ACN0 = 1ULL << 41U-End--> |
| AMBISONICS_ACN1 = 1ULL << 42U | 一阶立体声声道数1<br><!--Device-AMBISONICS_ACN1 = 1ULL << 42U--><!--Device-AMBISONICS_ACN1 = 1ULL << 42U-End--> |
| AMBISONICS_ACN2 = 1ULL << 43U | 一阶立体声声道数2<br><!--Device-AMBISONICS_ACN2 = 1ULL << 43U--><!--Device-AMBISONICS_ACN2 = 1ULL << 43U-End--> |
| AMBISONICS_ACN3 = 1ULL << 44U | 一阶立体声声道数3<br><!--Device-AMBISONICS_ACN3 = 1ULL << 44U--><!--Device-AMBISONICS_ACN3 = 1ULL << 44U-End--> |
| AMBISONICS_W = AMBISONICS_ACN0 | 同于零阶立体声声道数0<br><!--Device-AMBISONICS_W = AMBISONICS_ACN0--><!--Device-AMBISONICS_W = AMBISONICS_ACN0-End--> |
| AMBISONICS_Y = AMBISONICS_ACN1 | 同于一阶立体声声道数1<br><!--Device-AMBISONICS_Y = AMBISONICS_ACN1--><!--Device-AMBISONICS_Y = AMBISONICS_ACN1-End--> |
| AMBISONICS_Z = AMBISONICS_ACN2 | 同于一阶立体声声道数2<br><!--Device-AMBISONICS_Z = AMBISONICS_ACN2--><!--Device-AMBISONICS_Z = AMBISONICS_ACN2-End--> |
| AMBISONICS_X = AMBISONICS_ACN3 | 同于一阶立体声声道数3<br><!--Device-AMBISONICS_X = AMBISONICS_ACN3--><!--Device-AMBISONICS_X = AMBISONICS_ACN3-End--> |
| AMBISONICS_ACN4 = 1ULL << 45U | 二阶立体声声道数4<br><!--Device-AMBISONICS_ACN4 = 1ULL << 45U--><!--Device-AMBISONICS_ACN4 = 1ULL << 45U-End--> |
| AMBISONICS_ACN5 = 1ULL << 46U | 二阶立体声声道数5<br><!--Device-AMBISONICS_ACN5 = 1ULL << 46U--><!--Device-AMBISONICS_ACN5 = 1ULL << 46U-End--> |
| AMBISONICS_ACN6 = 1ULL << 47U | 二阶立体声声道数6<br><!--Device-AMBISONICS_ACN6 = 1ULL << 47U--><!--Device-AMBISONICS_ACN6 = 1ULL << 47U-End--> |
| AMBISONICS_ACN7 = 1ULL << 48U | 二阶立体声声道数7<br><!--Device-AMBISONICS_ACN7 = 1ULL << 48U--><!--Device-AMBISONICS_ACN7 = 1ULL << 48U-End--> |
| AMBISONICS_ACN8 = 1ULL << 49U | 二阶立体声声道数8<br><!--Device-AMBISONICS_ACN8 = 1ULL << 49U--><!--Device-AMBISONICS_ACN8 = 1ULL << 49U-End--> |
| AMBISONICS_ACN9 = 1ULL << 50U | 三阶立体声声道数9<br><!--Device-AMBISONICS_ACN9 = 1ULL << 50U--><!--Device-AMBISONICS_ACN9 = 1ULL << 50U-End--> |
| AMBISONICS_ACN10 = 1ULL << 51U | 三阶立体声声道数10<br><!--Device-AMBISONICS_ACN10 = 1ULL << 51U--><!--Device-AMBISONICS_ACN10 = 1ULL << 51U-End--> |
| AMBISONICS_ACN11 = 1ULL << 52U | 三阶立体声声道数11<br><!--Device-AMBISONICS_ACN11 = 1ULL << 52U--><!--Device-AMBISONICS_ACN11 = 1ULL << 52U-End--> |
| AMBISONICS_ACN12 = 1ULL << 53U | 三阶立体声声道数12<br><!--Device-AMBISONICS_ACN12 = 1ULL << 53U--><!--Device-AMBISONICS_ACN12 = 1ULL << 53U-End--> |
| AMBISONICS_ACN13 = 1ULL << 54U | 三阶立体声声道数13<br><!--Device-AMBISONICS_ACN13 = 1ULL << 54U--><!--Device-AMBISONICS_ACN13 = 1ULL << 54U-End--> |
| AMBISONICS_ACN14 = 1ULL << 55U | 三阶立体声声道数14<br><!--Device-AMBISONICS_ACN14 = 1ULL << 55U--><!--Device-AMBISONICS_ACN14 = 1ULL << 55U-End--> |
| AMBISONICS_ACN15 = 1ULL << 56U | 三阶立体声声道数15<br><!--Device-AMBISONICS_ACN15 = 1ULL << 56U--><!--Device-AMBISONICS_ACN15 = 1ULL << 56U-End--> |

### AudioChannelLayout

```c
enum AudioChannelLayout : uint64_t
```

**描述：**

音频声道数类型，将用户申请的解码器输出格式表示为编解码器的声道类型。

<!--Device-enum AudioChannelLayout : uint64_t--><!--Device-enum AudioChannelLayout : uint64_t-End-->

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 10

**废弃版本：** 11

**替代接口：** OH_AudioChannelLayout

| 枚举项 | 描述 |
| -- | -- |
| UNKNOWN_CHANNEL_LAYOUT = 0 | <!--Device-UNKNOWN_CHANNEL_LAYOUT = 0--><!--Device-UNKNOWN_CHANNEL_LAYOUT = 0-End--> |
| MONO = (AudioChannelSet::FRONT_CENTER) | <!--Device-MONO = (AudioChannelSet::FRONT_CENTER)--><!--Device-MONO = (AudioChannelSet::FRONT_CENTER)-End--> |
| STEREO = (AudioChannelSet::FRONT_LEFT \| AudioChannelSet::FRONT_RIGHT) | <!--Device-STEREO = (AudioChannelSet::FRONT_LEFT \| AudioChannelSet::FRONT_RIGHT)--><!--Device-STEREO = (AudioChannelSet::FRONT_LEFT \| AudioChannelSet::FRONT_RIGHT)-End--> |
| CH_2POINT1 = (STEREO \| AudioChannelSet::LOW_FREQUENCY) | <!--Device-CH_2POINT1 = (STEREO \| AudioChannelSet::LOW_FREQUENCY)--><!--Device-CH_2POINT1 = (STEREO \| AudioChannelSet::LOW_FREQUENCY)-End--> |
| CH_2_1 = (STEREO \| AudioChannelSet::BACK_CENTER) | <!--Device-CH_2_1 = (STEREO \| AudioChannelSet::BACK_CENTER)--><!--Device-CH_2_1 = (STEREO \| AudioChannelSet::BACK_CENTER)-End--> |
| SURROUND = (STEREO \| AudioChannelSet::FRONT_CENTER) | <!--Device-SURROUND = (STEREO \| AudioChannelSet::FRONT_CENTER)--><!--Device-SURROUND = (STEREO \| AudioChannelSet::FRONT_CENTER)-End--> |
| CH_3POINT1 = (SURROUND \| AudioChannelSet::LOW_FREQUENCY) | <!--Device-CH_3POINT1 = (SURROUND \| AudioChannelSet::LOW_FREQUENCY)--><!--Device-CH_3POINT1 = (SURROUND \| AudioChannelSet::LOW_FREQUENCY)-End--> |
| CH_4POINT0 = (SURROUND \| AudioChannelSet::BACK_CENTER) | <!--Device-CH_4POINT0 = (SURROUND \| AudioChannelSet::BACK_CENTER)--><!--Device-CH_4POINT0 = (SURROUND \| AudioChannelSet::BACK_CENTER)-End--> |
| CH_4POINT1 = (CH_4POINT0 \| AudioChannelSet::LOW_FREQUENCY) | <!--Device-CH_4POINT1 = (CH_4POINT0 \| AudioChannelSet::LOW_FREQUENCY)--><!--Device-CH_4POINT1 = (CH_4POINT0 \| AudioChannelSet::LOW_FREQUENCY)-End--> |
| CH_2_2 = (STEREO \| AudioChannelSet::SIDE_LEFT \| AudioChannelSet::SIDE_RIGHT) | <!--Device-CH_2_2 = (STEREO \| AudioChannelSet::SIDE_LEFT \| AudioChannelSet::SIDE_RIGHT)--><!--Device-CH_2_2 = (STEREO \| AudioChannelSet::SIDE_LEFT \| AudioChannelSet::SIDE_RIGHT)-End--> |
| QUAD = (STEREO \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT) | <!--Device-QUAD = (STEREO \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT)--><!--Device-QUAD = (STEREO \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT)-End--> |
| CH_5POINT0 = (SURROUND \| AudioChannelSet::SIDE_LEFT \| AudioChannelSet::SIDE_RIGHT) | <!--Device-CH_5POINT0 = (SURROUND \| AudioChannelSet::SIDE_LEFT \| AudioChannelSet::SIDE_RIGHT)--><!--Device-CH_5POINT0 = (SURROUND \| AudioChannelSet::SIDE_LEFT \| AudioChannelSet::SIDE_RIGHT)-End--> |
| CH_5POINT1 = (CH_5POINT0 \| AudioChannelSet::LOW_FREQUENCY) | <!--Device-CH_5POINT1 = (CH_5POINT0 \| AudioChannelSet::LOW_FREQUENCY)--><!--Device-CH_5POINT1 = (CH_5POINT0 \| AudioChannelSet::LOW_FREQUENCY)-End--> |
| CH_5POINT0_BACK = (SURROUND \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT) | <!--Device-CH_5POINT0_BACK = (SURROUND \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT)--><!--Device-CH_5POINT0_BACK = (SURROUND \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT)-End--> |
| CH_5POINT1_BACK = (CH_5POINT0_BACK \| AudioChannelSet::LOW_FREQUENCY) | <!--Device-CH_5POINT1_BACK = (CH_5POINT0_BACK \| AudioChannelSet::LOW_FREQUENCY)--><!--Device-CH_5POINT1_BACK = (CH_5POINT0_BACK \| AudioChannelSet::LOW_FREQUENCY)-End--> |
| CH_6POINT0 = (CH_5POINT0 \| AudioChannelSet::BACK_CENTER) | <!--Device-CH_6POINT0 = (CH_5POINT0 \| AudioChannelSet::BACK_CENTER)--><!--Device-CH_6POINT0 = (CH_5POINT0 \| AudioChannelSet::BACK_CENTER)-End--> |
| CH_6POINT0_FRONT = (CH_2_2 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER) | <!--Device-CH_6POINT0_FRONT = (CH_2_2 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER)--><!--Device-CH_6POINT0_FRONT = (CH_2_2 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER)-End--> |
| HEXAGONAL = (CH_5POINT0_BACK \| AudioChannelSet::BACK_CENTER) | <!--Device-HEXAGONAL = (CH_5POINT0_BACK \| AudioChannelSet::BACK_CENTER)--><!--Device-HEXAGONAL = (CH_5POINT0_BACK \| AudioChannelSet::BACK_CENTER)-End--> |
| CH_6POINT1 = (CH_5POINT1 \| AudioChannelSet::BACK_CENTER) | <!--Device-CH_6POINT1 = (CH_5POINT1 \| AudioChannelSet::BACK_CENTER)--><!--Device-CH_6POINT1 = (CH_5POINT1 \| AudioChannelSet::BACK_CENTER)-End--> |
| CH_6POINT1_BACK = (CH_5POINT1_BACK \| AudioChannelSet::BACK_CENTER) | <!--Device-CH_6POINT1_BACK = (CH_5POINT1_BACK \| AudioChannelSet::BACK_CENTER)--><!--Device-CH_6POINT1_BACK = (CH_5POINT1_BACK \| AudioChannelSet::BACK_CENTER)-End--> |
| CH_6POINT1_FRONT = (CH_6POINT0_FRONT \| AudioChannelSet::LOW_FREQUENCY) | <!--Device-CH_6POINT1_FRONT = (CH_6POINT0_FRONT \| AudioChannelSet::LOW_FREQUENCY)--><!--Device-CH_6POINT1_FRONT = (CH_6POINT0_FRONT \| AudioChannelSet::LOW_FREQUENCY)-End--> |
| CH_7POINT0 = (CH_5POINT0 \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT) | <!--Device-CH_7POINT0 = (CH_5POINT0 \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT)--><!--Device-CH_7POINT0 = (CH_5POINT0 \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT)-End--> |
| CH_7POINT0_FRONT = (CH_5POINT0 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER) | <!--Device-CH_7POINT0_FRONT = (CH_5POINT0 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER)--><!--Device-CH_7POINT0_FRONT = (CH_5POINT0 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER)-End--> |
| CH_7POINT1 = (CH_5POINT1 \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT) | <!--Device-CH_7POINT1 = (CH_5POINT1 \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT)--><!--Device-CH_7POINT1 = (CH_5POINT1 \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT)-End--> |
| CH_7POINT1_WIDE = (CH_5POINT1 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER) | <!--Device-CH_7POINT1_WIDE = (CH_5POINT1 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER)--><!--Device-CH_7POINT1_WIDE = (CH_5POINT1 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER)-End--> |
| CH_7POINT1_WIDE_BACK = (CH_5POINT1_BACK \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER) | <!--Device-CH_7POINT1_WIDE_BACK = (CH_5POINT1_BACK \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER)--><!--Device-CH_7POINT1_WIDE_BACK = (CH_5POINT1_BACK \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER)-End--> |
| CH_3POINT1POINT2 = (CH_3POINT1 \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT) | <!--Device-CH_3POINT1POINT2 = (CH_3POINT1 \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT)--><!--Device-CH_3POINT1POINT2 = (CH_3POINT1 \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT)-End--> |
| CH_5POINT1POINT2 = (CH_5POINT1 \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT) | <!--Device-CH_5POINT1POINT2 = (CH_5POINT1 \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT)--><!--Device-CH_5POINT1POINT2 = (CH_5POINT1 \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT)-End--> |
| CH_5POINT1POINT4 = (CH_5POINT1 \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT \| AudioChannelSet::TOP_BACK_LEFT \| AudioChannelSet::TOP_BACK_RIGHT) | <!--Device-CH_5POINT1POINT4 = (CH_5POINT1 \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT \| AudioChannelSet::TOP_BACK_LEFT \| AudioChannelSet::TOP_BACK_RIGHT)--><!--Device-CH_5POINT1POINT4 = (CH_5POINT1 \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT \| AudioChannelSet::TOP_BACK_LEFT \| AudioChannelSet::TOP_BACK_RIGHT)-End--> |
| CH_7POINT1POINT2 = (CH_7POINT1 \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT) | <!--Device-CH_7POINT1POINT2 = (CH_7POINT1 \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT)--><!--Device-CH_7POINT1POINT2 = (CH_7POINT1 \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT)-End--> |
| CH_7POINT1POINT4 = (CH_7POINT1 \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT \| AudioChannelSet::TOP_BACK_LEFT \| AudioChannelSet::TOP_BACK_RIGHT) | <!--Device-CH_7POINT1POINT4 = (CH_7POINT1 \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT \| AudioChannelSet::TOP_BACK_LEFT \| AudioChannelSet::TOP_BACK_RIGHT)--><!--Device-CH_7POINT1POINT4 = (CH_7POINT1 \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT \| AudioChannelSet::TOP_BACK_LEFT \| AudioChannelSet::TOP_BACK_RIGHT)-End--> |
| CH_9POINT1POINT4 = (CH_7POINT1POINT4 \| AudioChannelSet::WIDE_LEFT \| AudioChannelSet::WIDE_RIGHT) | <!--Device-CH_9POINT1POINT4 = (CH_7POINT1POINT4 \| AudioChannelSet::WIDE_LEFT \| AudioChannelSet::WIDE_RIGHT)--><!--Device-CH_9POINT1POINT4 = (CH_7POINT1POINT4 \| AudioChannelSet::WIDE_LEFT \| AudioChannelSet::WIDE_RIGHT)-End--> |
| CH_9POINT1POINT6 = (CH_9POINT1POINT4 \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT) | <!--Device-CH_9POINT1POINT6 = (CH_9POINT1POINT4 \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT)--><!--Device-CH_9POINT1POINT6 = (CH_9POINT1POINT4 \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT)-End--> |
| CH_10POINT2 = (AudioChannelSet::FRONT_LEFT \| AudioChannelSet::FRONT_RIGHT \| AudioChannelSet::FRONT_CENTER \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT \| AudioChannelSet::BACK_CENTER \| AudioChannelSet::SIDE_LEFT \| AudioChannelSet::SIDE_RIGHT \| AudioChannelSet::WIDE_LEFT \| AudioChannelSet::WIDE_RIGHT) | <!--Device-CH_10POINT2 = (AudioChannelSet::FRONT_LEFT \| AudioChannelSet::FRONT_RIGHT \| AudioChannelSet::FRONT_CENTER \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT \| AudioChannelSet::BACK_CENTER \| AudioChannelSet::SIDE_LEFT \| AudioChannelSet::SIDE_RIGHT \| AudioChannelSet::WIDE_LEFT \| AudioChannelSet::WIDE_RIGHT)--><!--Device-CH_10POINT2 = (AudioChannelSet::FRONT_LEFT \| AudioChannelSet::FRONT_RIGHT \| AudioChannelSet::FRONT_CENTER \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT \| AudioChannelSet::BACK_CENTER \| AudioChannelSet::SIDE_LEFT \| AudioChannelSet::SIDE_RIGHT \| AudioChannelSet::WIDE_LEFT \| AudioChannelSet::WIDE_RIGHT)-End--> |
| CH_22POINT2 = (CH_7POINT1POINT4 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER \| AudioChannelSet::BACK_CENTER \| AudioChannelSet::TOP_CENTER \| AudioChannelSet::TOP_FRONT_CENTER \| AudioChannelSet::TOP_BACK_CENTER \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT \| AudioChannelSet::BOTTOM_FRONT_LEFT \| AudioChannelSet::BOTTOM_FRONT_RIGHT \| AudioChannelSet::BOTTOM_FRONT_CENTER \| AudioChannelSet::LOW_FREQUENCY_2) | <!--Device-CH_22POINT2 = (CH_7POINT1POINT4 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER \| AudioChannelSet::BACK_CENTER \| AudioChannelSet::TOP_CENTER \| AudioChannelSet::TOP_FRONT_CENTER \| AudioChannelSet::TOP_BACK_CENTER \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT \| AudioChannelSet::BOTTOM_FRONT_LEFT \| AudioChannelSet::BOTTOM_FRONT_RIGHT \| AudioChannelSet::BOTTOM_FRONT_CENTER \| AudioChannelSet::LOW_FREQUENCY_2)--><!--Device-CH_22POINT2 = (CH_7POINT1POINT4 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER \| AudioChannelSet::BACK_CENTER \| AudioChannelSet::TOP_CENTER \| AudioChannelSet::TOP_FRONT_CENTER \| AudioChannelSet::TOP_BACK_CENTER \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT \| AudioChannelSet::BOTTOM_FRONT_LEFT \| AudioChannelSet::BOTTOM_FRONT_RIGHT \| AudioChannelSet::BOTTOM_FRONT_CENTER \| AudioChannelSet::LOW_FREQUENCY_2)-End--> |
| OCTAGONAL = (CH_5POINT0 \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_CENTER \| AudioChannelSet::BACK_RIGHT) | <!--Device-OCTAGONAL = (CH_5POINT0 \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_CENTER \| AudioChannelSet::BACK_RIGHT)--><!--Device-OCTAGONAL = (CH_5POINT0 \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_CENTER \| AudioChannelSet::BACK_RIGHT)-End--> |
| HEXADECAGONAL = (OCTAGONAL \| AudioChannelSet::WIDE_LEFT \| AudioChannelSet::WIDE_RIGHT \| AudioChannelSet::TOP_BACK_LEFT \| AudioChannelSet::TOP_BACK_RIGHT \| AudioChannelSet::TOP_BACK_CENTER \| AudioChannelSet::TOP_FRONT_CENTER \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT) | <!--Device-HEXADECAGONAL = (OCTAGONAL \| AudioChannelSet::WIDE_LEFT \| AudioChannelSet::WIDE_RIGHT \| AudioChannelSet::TOP_BACK_LEFT \| AudioChannelSet::TOP_BACK_RIGHT \| AudioChannelSet::TOP_BACK_CENTER \| AudioChannelSet::TOP_FRONT_CENTER \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT)--><!--Device-HEXADECAGONAL = (OCTAGONAL \| AudioChannelSet::WIDE_LEFT \| AudioChannelSet::WIDE_RIGHT \| AudioChannelSet::TOP_BACK_LEFT \| AudioChannelSet::TOP_BACK_RIGHT \| AudioChannelSet::TOP_BACK_CENTER \| AudioChannelSet::TOP_FRONT_CENTER \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT)-End--> |
| STEREO_DOWNMIX = (AudioChannelSet::STEREO_LEFT \| AudioChannelSet::STEREO_RIGHT) | <!--Device-STEREO_DOWNMIX = (AudioChannelSet::STEREO_LEFT \| AudioChannelSet::STEREO_RIGHT)--><!--Device-STEREO_DOWNMIX = (AudioChannelSet::STEREO_LEFT \| AudioChannelSet::STEREO_RIGHT)-End--> |
| HOA_FIRST = AudioChannelSet::AMBISONICS_ACN0 \| AudioChannelSet::AMBISONICS_ACN1 \| AudioChannelSet::AMBISONICS_ACN2 \| AudioChannelSet::AMBISONICS_ACN3 | <!--Device-HOA_FIRST = AudioChannelSet::AMBISONICS_ACN0 \| AudioChannelSet::AMBISONICS_ACN1 \| AudioChannelSet::AMBISONICS_ACN2 \| AudioChannelSet::AMBISONICS_ACN3--><!--Device-HOA_FIRST = AudioChannelSet::AMBISONICS_ACN0 \| AudioChannelSet::AMBISONICS_ACN1 \| AudioChannelSet::AMBISONICS_ACN2 \| AudioChannelSet::AMBISONICS_ACN3-End--> |
| HOA_SECOND = HOA_FIRST \| AudioChannelSet::AMBISONICS_ACN4 \| AudioChannelSet::AMBISONICS_ACN5 \| AudioChannelSet::AMBISONICS_ACN6 \| AudioChannelSet::AMBISONICS_ACN7 \| AudioChannelSet::AMBISONICS_ACN8 | <!--Device-HOA_SECOND = HOA_FIRST \| AudioChannelSet::AMBISONICS_ACN4 \| AudioChannelSet::AMBISONICS_ACN5 \| AudioChannelSet::AMBISONICS_ACN6 \| AudioChannelSet::AMBISONICS_ACN7 \| AudioChannelSet::AMBISONICS_ACN8--><!--Device-HOA_SECOND = HOA_FIRST \| AudioChannelSet::AMBISONICS_ACN4 \| AudioChannelSet::AMBISONICS_ACN5 \| AudioChannelSet::AMBISONICS_ACN6 \| AudioChannelSet::AMBISONICS_ACN7 \| AudioChannelSet::AMBISONICS_ACN8-End--> |
| HOA_THIRD = HOA_SECOND \| AudioChannelSet::AMBISONICS_ACN9 \| AudioChannelSet::AMBISONICS_ACN10 \| AudioChannelSet::AMBISONICS_ACN11 \| AudioChannelSet::AMBISONICS_ACN12 \| AudioChannelSet::AMBISONICS_ACN13 \| AudioChannelSet::AMBISONICS_ACN14 \| AudioChannelSet::AMBISONICS_ACN15 | <!--Device-HOA_THIRD = HOA_SECOND \| AudioChannelSet::AMBISONICS_ACN9 \| AudioChannelSet::AMBISONICS_ACN10 \| AudioChannelSet::AMBISONICS_ACN11 \| AudioChannelSet::AMBISONICS_ACN12 \| AudioChannelSet::AMBISONICS_ACN13 \| AudioChannelSet::AMBISONICS_ACN14 \| AudioChannelSet::AMBISONICS_ACN15--><!--Device-HOA_THIRD = HOA_SECOND \| AudioChannelSet::AMBISONICS_ACN9 \| AudioChannelSet::AMBISONICS_ACN10 \| AudioChannelSet::AMBISONICS_ACN11 \| AudioChannelSet::AMBISONICS_ACN12 \| AudioChannelSet::AMBISONICS_ACN13 \| AudioChannelSet::AMBISONICS_ACN14 \| AudioChannelSet::AMBISONICS_ACN15-End--> |


