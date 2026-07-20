# AVMetadata

媒体元数据的相关属性。

**起始版本：** 10

<!--Device-avSession-interface AVMetadata--><!--Device-avSession-interface AVMetadata-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## album

```TypeScript
album?: string
```

专辑名称。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-album?: string--><!--Device-AVMetadata-album?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## artist

```TypeScript
artist?: string
```

艺术家。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-artist?: string--><!--Device-AVMetadata-artist?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## assetId

```TypeScript
assetId: string
```

媒体ID。媒体信息的唯一标识，由应用自定义。

- 该属性发生变化则其他元数据属性都将被刷新。  
- 若该属性维持不变，且不设置相应的媒体元数据信息，那么将不会更新对应的媒体元数据信息。  
- 当该属性设为空值时，调用[setAVMetadata](arkts-avsession-avsession-avsession-i.md#setavmetadata-1)方法将失败，返回错误码6600101。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-assetId: string--><!--Device-AVMetadata-assetId: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## author

```TypeScript
author?: string
```

专辑作者。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-author?: string--><!--Device-AVMetadata-author?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## avQueueId

```TypeScript
avQueueId?: string
```

歌单（歌曲列表）唯一标识Id。

**类型：** string

**起始版本：** 11

<!--Device-AVMetadata-avQueueId?: string--><!--Device-AVMetadata-avQueueId?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## avQueueImage

```TypeScript
avQueueImage?: image.PixelMap | string
```

歌单（歌曲列表）封面图。

图片的像素数据或者图片路径地址（本地路径或网络路径）。应用通过setAVMetadata设置图片数据。

- 设置的数据类型为PixelMap时，通过getAVMetadata获取的将为PixelMap。  
- 设置为url图片路径，获取的为url图片路径。

**类型：** image.PixelMap \| string

**起始版本：** 11

<!--Device-AVMetadata-avQueueImage?: image.PixelMap | string--><!--Device-AVMetadata-avQueueImage?: image.PixelMap | string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## avQueueName

```TypeScript
avQueueName?: string
```

歌单（歌曲列表）名称。

**类型：** string

**起始版本：** 12

<!--Device-AVMetadata-avQueueName?: string--><!--Device-AVMetadata-avQueueName?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## bundleIcon

```TypeScript
readonly bundleIcon?: image.PixelMap
```

应用图标图片的像素数据。只读类型，不从应用侧设置。

**类型：** image.PixelMap

**起始版本：** 18

<!--Device-AVMetadata-readonly bundleIcon?: image.PixelMap--><!--Device-AVMetadata-readonly bundleIcon?: image.PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## composer

```TypeScript
composer?: string
```

作曲者。

**类型：** string

**起始版本：** 10

<!--Device-AVMetadata-composer?: string--><!--Device-AVMetadata-composer?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## description

```TypeScript
description?: string
```

媒体描述。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-description?: string--><!--Device-AVMetadata-description?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## displayTags

```TypeScript
displayTags?: number
```

媒体资源的金标类型，取值参考[DisplayTag](arkts-avsession-avsession-displaytag-e.md)。

**类型：** number

**起始版本：** 11

<!--Device-AVMetadata-displayTags?: int--><!--Device-AVMetadata-displayTags?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## drmSchemes

```TypeScript
drmSchemes?: Array<string>
```

当前session支持的DRM方案，取值为DRM方案uuid。

**类型：** Array&lt;string&gt;

**起始版本：** 12

<!--Device-AVMetadata-drmSchemes?: Array<string>--><!--Device-AVMetadata-drmSchemes?: Array<string>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## duration

```TypeScript
duration?: number
```

媒体时长，单位毫秒（ms）。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-duration?: long--><!--Device-AVMetadata-duration?: long-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## fastForwardSkipIntervals

```TypeScript
fastForwardSkipIntervals?: SkipIntervals
```

快进支持的时间间隔。默认为SECONDS_15，即15秒。

系统会使用此值作为快进操作的时间间隔，而非skipIntervals的值。

若未设置此参数，快进操作的时间间隔仍会沿用skipIntervals的值。

**起始版本**：26.0.0

**类型：** SkipIntervals

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMetadata-fastForwardSkipIntervals?: SkipIntervals--><!--Device-AVMetadata-fastForwardSkipIntervals?: SkipIntervals-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## filter

```TypeScript
filter?: number
```

当前会话支持的协议，默认为TYPE_CAST_PLUS_STREAM。具体取值参考[ProtocolType](arkts-avsession-avsession-protocoltype-e.md)。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-filter?: int--><!--Device-AVMetadata-filter?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## lyric

```TypeScript
lyric?: string
```

媒体歌词内容。应用需将歌词内容拼接为一个字符串传入。

字符串长度需小于40960字节。

**说明：** 系统支持简单版的LRC格式（Simple LRC format）的歌词文本内容。当传入的歌词内容不规范（例如：出现重复的时间戳等），将导致解析失败，并在系统中显示异常。

**类型：** string

**起始版本：** 10

<!--Device-AVMetadata-lyric?: string--><!--Device-AVMetadata-lyric?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## mediaImage

```TypeScript
mediaImage?: image.PixelMap | string
```

图片的像素数据或者图片路径地址（本地路径或网络路径）。应用通过setAVMetadata设置图片数据。

- 设置的数据类型为PixelMap时，通过getAVMetadata获取的将为PixelMap。  
- 设置为url图片路径，获取的为url图片路径。

**类型：** image.PixelMap \| string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-mediaImage?: image.PixelMap | string--><!--Device-AVMetadata-mediaImage?: image.PixelMap | string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## nextAssetId

```TypeScript
nextAssetId?: string
```

下一首媒体ID。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-nextAssetId?: string--><!--Device-AVMetadata-nextAssetId?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## previousAssetId

```TypeScript
previousAssetId?: string
```

上一首媒体ID。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-previousAssetId?: string--><!--Device-AVMetadata-previousAssetId?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## publishDate

```TypeScript
publishDate?: Date
```

发行日期。

**类型：** Date

**起始版本：** 10

<!--Device-AVMetadata-publishDate?: Date--><!--Device-AVMetadata-publishDate?: Date-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## rewindSkipIntervals

```TypeScript
rewindSkipIntervals?: SkipIntervals
```

快退支持的时间间隔。默认为SECONDS_15，即15秒。

系统会使用此值作为快退操作的时间间隔，而非skipIntervals的值。

若未设置此参数，快退操作的时间间隔仍会沿用skipIntervals的值。

**起始版本**：26.0.0

**类型：** SkipIntervals

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVMetadata-rewindSkipIntervals?: SkipIntervals--><!--Device-AVMetadata-rewindSkipIntervals?: SkipIntervals-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## singleLyricText

```TypeScript
singleLyricText?: string
```

单条媒体歌词内容。应用需将歌词内容拼接为一个字符串传入（不包含时间戳）。

字符串长度小于40960字节。

**类型：** string

**起始版本：** 17

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-singleLyricText?: string--><!--Device-AVMetadata-singleLyricText?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## skipIntervals

```TypeScript
skipIntervals?: SkipIntervals
```

快进快退支持的时间间隔。默认为SECONDS_15，即15秒。

**类型：** SkipIntervals

**起始版本：** 11

<!--Device-AVMetadata-skipIntervals?: SkipIntervals--><!--Device-AVMetadata-skipIntervals?: SkipIntervals-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## subtitle

```TypeScript
subtitle?: string
```

子标题。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-subtitle?: string--><!--Device-AVMetadata-subtitle?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## title

```TypeScript
title?: string
```

标题。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-title?: string--><!--Device-AVMetadata-title?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## writer

```TypeScript
writer?: string
```

词作者。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMetadata-writer?: string--><!--Device-AVMetadata-writer?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

