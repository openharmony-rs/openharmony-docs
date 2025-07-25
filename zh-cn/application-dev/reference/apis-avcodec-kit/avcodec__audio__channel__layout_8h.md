# avcodec_audio_channel_layout.h


## 概述

音频编解码枚举的声明。

**库：** libnative_media_codecbase.so

**引用文件：** <multimedia/player_framework/avcodec_audio_channel_layout.h>

**起始版本：** 9

**废弃版本：** 11

**相关模块：**[CodecBase](_codec_base.md)


## 汇总


### 枚举

| 名称 | 描述 | 
| -------- | -------- |
| [AudioChannelSet](_codec_base.md#audiochannelset) : uint64_t {<br/>FRONT_LEFT = 1ULL &lt;&lt; 0U,<br/>FRONT_RIGHT = 1ULL &lt;&lt; 1U,<br/>FRONT_CENTER = 1ULL &lt;&lt; 2U,<br/>LOW_FREQUENCY = 1ULL &lt;&lt; 3U,<br/>BACK_LEFT = 1ULL &lt;&lt; 4U,<br/>BACK_RIGHT = 1ULL &lt;&lt; 5U,<br/>FRONT_LEFT_OF_CENTER = 1ULL &lt;&lt; 6U,<br/>FRONT_RIGHT_OF_CENTER = 1ULL &lt;&lt; 7U,<br/>BACK_CENTER = 1ULL &lt;&lt; 8U,<br/>SIDE_LEFT = 1ULL &lt;&lt; 9U,<br/>SIDE_RIGHT = 1ULL &lt;&lt; 10U,<br/>TOP_CENTER = 1ULL &lt;&lt; 11U,<br/>TOP_FRONT_LEFT = 1ULL &lt;&lt; 12U,<br/>TOP_FRONT_CENTER = 1ULL &lt;&lt; 13U,<br/>TOP_FRONT_RIGHT = 1ULL &lt;&lt; 14U,<br/>TOP_BACK_LEFT = 1ULL &lt;&lt; 15U,<br/>TOP_BACK_CENTER = 1ULL &lt;&lt; 16U,<br/>TOP_BACK_RIGHT = 1ULL &lt;&lt; 17U,<br/>STEREO_LEFT = 1ULL &lt;&lt; 29U,<br/>STEREO_RIGHT = 1ULL &lt;&lt; 30U,<br/>WIDE_LEFT = 1ULL &lt;&lt; 31U,<br/>WIDE_RIGHT = 1ULL &lt;&lt; 32U,<br/>SURROUND_DIRECT_LEFT = 1ULL &lt;&lt; 33U,<br/>SURROUND_DIRECT_RIGHT = 1ULL &lt;&lt; 34U,<br/>LOW_FREQUENCY_2 = 1ULL &lt;&lt; 35U,<br/>TOP_SIDE_LEFT = 1ULL &lt;&lt; 36U,<br/>TOP_SIDE_RIGHT = 1ULL &lt;&lt; 37U,<br/>BOTTOM_FRONT_CENTER = 1ULL &lt;&lt; 38U,<br/>BOTTOM_FRONT_LEFT = 1ULL &lt;&lt; 39U,<br/>BOTTOM_FRONT_RIGHT = 1ULL &lt;&lt; 40U,<br/>AMBISONICS_ACN0 = 1ULL &lt;&lt; 41U,<br/>AMBISONICS_ACN1 = 1ULL &lt;&lt; 42U,<br/>AMBISONICS_ACN2 = 1ULL &lt;&lt; 43U,<br/>AMBISONICS_ACN3 = 1ULL &lt;&lt; 44U,<br/>AMBISONICS_W = AMBISONICS_ACN0,<br/>AMBISONICS_Y = AMBISONICS_ACN1,<br/>AMBISONICS_Z = AMBISONICS_ACN2,<br/>AMBISONICS_X = AMBISONICS_ACN3,<br/>AMBISONICS_ACN4 = 1ULL &lt;&lt; 45U,<br/>AMBISONICS_ACN5 = 1ULL &lt;&lt; 46U,<br/>AMBISONICS_ACN6 = 1ULL &lt;&lt; 47U,<br/>AMBISONICS_ACN7 = 1ULL &lt;&lt; 48U,<br/>AMBISONICS_ACN8 = 1ULL &lt;&lt; 49U,<br/>AMBISONICS_ACN9 = 1ULL &lt;&lt; 50U,<br/>AMBISONICS_ACN10 = 1ULL &lt;&lt; 51U,<br/>AMBISONICS_ACN11 = 1ULL &lt;&lt; 52U,<br/>AMBISONICS_ACN12 = 1ULL &lt;&lt; 53U,<br/>AMBISONICS_ACN13 = 1ULL &lt;&lt; 54U,<br/>AMBISONICS_ACN14 = 1ULL &lt;&lt; 55U,<br/>AMBISONICS_ACN15 = 1ULL &lt;&lt; 56U<br/>} | 音频声道数集合，将每一个声道数映射为int64的变量。 | 
| [AudioChannelLayout](_codec_base.md#audiochannellayout) : uint64_t {<br/>UNKNOWN_CHANNEL_LAYOUT = 0,<br/>MONO = (AudioChannelSet::FRONT_CENTER),<br/>STEREO = (AudioChannelSet::FRONT_LEFT \| AudioChannelSet::FRONT_RIGHT),<br/>CH_2POINT1 = (STEREO \| AudioChannelSet::LOW_FREQUENCY),<br/>CH_2_1 = (STEREO \| AudioChannelSet::BACK_CENTER),<br/>SURROUND = (STEREO \| AudioChannelSet::FRONT_CENTER),<br/>CH_3POINT1 = (SURROUND \| AudioChannelSet::LOW_FREQUENCY),<br/>CH_4POINT0 = (SURROUND \| AudioChannelSet::BACK_CENTER),<br/>CH_4POINT1 = (CH_4POINT0 \| AudioChannelSet::LOW_FREQUENCY),<br/>CH_2_2 = (STEREO \| AudioChannelSet::SIDE_LEFT \| AudioChannelSet::SIDE_RIGHT),<br/>QUAD = (STEREO \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT),<br/>CH_5POINT0 = (SURROUND \| AudioChannelSet::SIDE_LEFT \| AudioChannelSet::SIDE_RIGHT),<br/>CH_5POINT1 = (CH_5POINT0 \| AudioChannelSet::LOW_FREQUENCY),<br/>CH_5POINT0_BACK = (SURROUND \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT),<br/>CH_5POINT1_BACK = (CH_5POINT0_BACK \| AudioChannelSet::LOW_FREQUENCY),<br/>CH_6POINT0 = (CH_5POINT0 \| AudioChannelSet::BACK_CENTER),<br/>CH_6POINT0_FRONT = (CH_2_2 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER),<br/>HEXAGONAL = (CH_5POINT0_BACK \| AudioChannelSet::BACK_CENTER),<br/>CH_6POINT1 = (CH_5POINT1 \| AudioChannelSet::BACK_CENTER),<br/>CH_6POINT1_BACK = (CH_5POINT1_BACK \| AudioChannelSet::BACK_CENTER),<br/>CH_6POINT1_FRONT = (CH_6POINT0_FRONT \| AudioChannelSet::LOW_FREQUENCY),<br/>CH_7POINT0 = (CH_5POINT0 \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT),<br/>CH_7POINT0_FRONT = (CH_5POINT0 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER),<br/>CH_7POINT1 = (CH_5POINT1 \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_RIGHT),<br/>CH_7POINT1_WIDE = (CH_5POINT1 \| AudioChannelSet::FRONT_LEFT_OF_CENTER \| AudioChannelSet::FRONT_RIGHT_OF_CENTER),<br/>CH_7POINT1_WIDE_BACK, CH_3POINT1POINT2 = (CH_3POINT1 \| AudioChannelSet::TOP_FRONT_LEFT \| AudioChannelSet::TOP_FRONT_RIGHT),<br/>CH_5POINT1POINT2 = (CH_5POINT1 \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT),<br/>CH_5POINT1POINT4, CH_7POINT1POINT2 = (CH_7POINT1 \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT),<br/>CH_7POINT1POINT4, CH_9POINT1POINT4 = (CH_7POINT1POINT4 \| AudioChannelSet::WIDE_LEFT \| AudioChannelSet::WIDE_RIGHT),<br/>CH_9POINT1POINT6 = (CH_9POINT1POINT4 \| AudioChannelSet::TOP_SIDE_LEFT \| AudioChannelSet::TOP_SIDE_RIGHT),<br/>CH_10POINT2, CH_22POINT2, OCTAGONAL = (CH_5POINT0 \| AudioChannelSet::BACK_LEFT \| AudioChannelSet::BACK_CENTER \| AudioChannelSet::BACK_RIGHT),<br/>HEXADECAGONAL, STEREO_DOWNMIX = (AudioChannelSet::STEREO_LEFT \| AudioChannelSet::STEREO_RIGHT),<br/>HOA_FIRST,<br/>HOA_SECOND,<br/>HOA_THIRD<br/>} | 音频声道数类型，将用户申请的解码器输出格式表示为编解码器的声道类型。 | 
