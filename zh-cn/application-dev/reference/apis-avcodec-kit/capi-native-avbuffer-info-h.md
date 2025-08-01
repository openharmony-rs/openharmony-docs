# native_avbuffer_info.h

## 概述

声明了媒体数据结构AVBuffer属性的定义。

**引用文件：** <multimedia/player_framework/native_avbuffer_info.h>

**库：** libnative_media_core.so

**系统能力：** SystemCapability.Multimedia.Media.Core

**起始版本：** 9

**相关模块：** [Core](capi-core.md)

**相关示例：** [AVCodec](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AVCodecBufferAttr](capi-core-oh-avcodecbufferattr.md) | OH_AVCodecBufferAttr | 定义OH_AVCodec的缓冲区描述信息。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AVCodecBufferFlags](#oh_avcodecbufferflags) | OH_AVCodecBufferFlags | 枚举OH_AVCodec缓冲区标记的类别。 |

## 枚举类型说明

### OH_AVCodecBufferFlags

```
enum OH_AVCodecBufferFlags
```

**描述**

枚举OH_AVCodec缓冲区标记的类别。

**系统能力：** SystemCapability.Multimedia.Media.Core

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| AVCODEC_BUFFER_FLAGS_NONE = 0 | 表示为普通帧。 |
| AVCODEC_BUFFER_FLAGS_EOS = 1 << 0 | 表示缓冲区是流结束帧。 |
| AVCODEC_BUFFER_FLAGS_SYNC_FRAME = 1 << 1 | 表示缓冲区包含关键帧。 |
| AVCODEC_BUFFER_FLAGS_INCOMPLETE_FRAME = 1 << 2 | 表示缓冲区中的数据只是帧的一部分。 |
| AVCODEC_BUFFER_FLAGS_CODEC_DATA = 1 << 3 | 表示缓冲区包含编解码特定数据。 |
| AVCODEC_BUFFER_FLAGS_DISCARD = 1 << 4 | 表示缓冲区被解码依赖，解码之后的数据可丢弃。<br>**起始版本：** 12 |
| AVCODEC_BUFFER_FLAGS_DISPOSABLE = 1 << 5 | 表示缓冲区不被参考可直接丢弃。<br>**起始版本：** 12 |


