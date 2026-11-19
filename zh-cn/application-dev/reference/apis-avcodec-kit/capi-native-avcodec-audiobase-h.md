# native_avcodec_audiobase.h
<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @mr-chencxy-->
<!--Designer: @dpy2650-->
<!--Tester: @baotianhao-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明用于基础音频编解码功能、音频特定配置和参数的Native API。

**引用文件：** <multimedia/player_framework/native_avcodec_audiobase.h>

**库：** libnative_media_codecbase.so

**系统能力：** SystemCapability.Multimedia.Media.CodecBase

**起始版本：** 26.1.0

**相关模块：** [CodecBase](capi-codecbase.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AVCodec_DSDCodecType](#oh_avcodec_dsdcodectype) | OH_AVCodec_DSDCodecType | DSD（Direct Stream Digital）编解码类型。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| const char *OH_MD_KEY_AUDIO_DSD_CODEC_TYPE | DSD解码类型的键，值类型为int32_t，取值请参见[OH_AVCodec_DSDCodecType](capi-native-avcodec-audiobase-h.md#oh_avcodec_dsdcodectype)。 该键是可选参数，只用来标记DSD解码类型，默认值为OH_AVCODEC_DSD_CODEC_LSBF_PLANAR(0)。<br>**起始版本：** 26.1.0 |

## 枚举类型说明

### OH_AVCodec_DSDCodecType

```c
enum OH_AVCodec_DSDCodecType
```

**描述：**

DSD（Direct Stream Digital）编解码类型。

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_AVCODEC_DSD_CODEC_LSBF_PLANAR = 0 | 适用于低位先行（LSB first）和平面排布的dsf容器格式。<br>**起始版本：** 26.1.0 |
| OH_AVCODEC_DSD_CODEC_MSBF_PLANAR = 1 | 适用于高位先行（MSB first）和平面排布的dsf容器格式。<br>**起始版本：** 26.1.0 |
| OH_AVCODEC_DSD_CODEC_MSBF = 2 | 适用于高位先行（MSB first）和交织排布的dff容器格式。<br>**起始版本：** 26.1.0 |


