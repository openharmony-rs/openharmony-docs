# AVMediaDescription

播放列表媒体元数据的相关属性。

**起始版本：** 23

<!--Device-avSession-interface AVMediaDescription--><!--Device-avSession-interface AVMediaDescription-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## albumCoverUri

```TypeScript
albumCoverUri?: string
```

播放列表媒体专辑封面URI。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-albumCoverUri?: string--><!--Device-AVMediaDescription-albumCoverUri?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## albumTitle

```TypeScript
albumTitle?: string
```

播放列表媒体专辑标题。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-albumTitle?: string--><!--Device-AVMediaDescription-albumTitle?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## appName

```TypeScript
appName?: string
```

播放列表提供的应用的名字。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-appName?: string--><!--Device-AVMediaDescription-appName?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## artist

```TypeScript
artist?: string
```

播放列表媒体专辑作者。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-artist?: string--><!--Device-AVMediaDescription-artist?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## assetId

```TypeScript
assetId: string
```

媒体ID。媒体信息的唯一标识，由应用自定义。 - 该属性发生变化则其他元数据属性都将被刷新。 - 若该属性维持不变，且不设置相应的媒体元数据信息，那么将不会更新对应的媒体元数据信息。 - 当该属性设为空值时，调用[setAVMetadata](arkts-avsession-avsession-avsession-i.md#setavmetadata)方法将失败，返回错误码6600101。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-assetId: string--><!--Device-AVMediaDescription-assetId: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## creditsPosition

```TypeScript
creditsPosition?: int
```

播放列表媒体的片尾播放位置。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-creditsPosition?: int--><!--Device-AVMediaDescription-creditsPosition?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## dataSrc

```TypeScript
dataSrc?: media.AVDataSrcDescriptor
```

播放列表数据源描述。

**类型：** media.AVDataSrcDescriptor

**起始版本：** 23

<!--Device-AVMediaDescription-dataSrc?: media.AVDataSrcDescriptor--><!--Device-AVMediaDescription-dataSrc?: media.AVDataSrcDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## description

```TypeScript
description?: string
```

播放列表媒体描述的文本。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-description?: string--><!--Device-AVMediaDescription-description?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## displayTags

```TypeScript
displayTags?: int
```

媒体资源的金标类型，取值参考[DisplayTag](arkts-avsession-avsession-displaytag-e.md)。 在使用了cast+协议的音频投播场景下，不支持使用该属性。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-displayTags?: int--><!--Device-AVMediaDescription-displayTags?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## drmScheme

```TypeScript
drmScheme?: string
```

播放列表媒体支持的DRM方案，由uuid表示。

**类型：** string

**起始版本：** 23

<!--Device-AVMediaDescription-drmScheme?: string--><!--Device-AVMediaDescription-drmScheme?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## duration

```TypeScript
duration?: int
```

播放列表媒体播放时长。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-duration?: int--><!--Device-AVMediaDescription-duration?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## extras

```TypeScript
extras?: Record<string, Object>
```

Any additional attributes that can be represented as key-value pairs

**类型：** Record&lt;string, Object&gt;

**起始版本：** 23

<!--Device-AVMediaDescription-extras?: Record<string, Object>--><!--Device-AVMediaDescription-extras?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## fdSrc

```TypeScript
fdSrc?: media.AVFileDescriptor
```

播放列表媒体本地文件的句柄。

**类型：** media.AVFileDescriptor

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-fdSrc?: media.AVFileDescriptor--><!--Device-AVMediaDescription-fdSrc?: media.AVFileDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## launchClientData

```TypeScript
launchClientData?: string
```

投播过程中应用程序向接收方发送的自定义数据。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-launchClientData?: string--><!--Device-AVMediaDescription-launchClientData?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## lyricContent

```TypeScript
lyricContent?: string
```

播放列表媒体歌词内容。 字符串长度需小于40960字节。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-lyricContent?: string--><!--Device-AVMediaDescription-lyricContent?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## lyricUri

```TypeScript
lyricUri?: string
```

播放列表媒体歌词URI。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-lyricUri?: string--><!--Device-AVMediaDescription-lyricUri?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## mediaImage

```TypeScript
mediaImage?: image.PixelMap | string
```

设置播放列表媒体图片像素数据。 在使用了cast+协议的音视频投播场景下，该字段用于给对端设备设置媒体专辑封面。 当入参为string类型时： - 只支持使用网络URI设置封面，不支持本地URI。 - 其作用与albumCoverUri属性功能相同，且优先级高于albumCoverUri。 从API version 23开始，支持入参为image.PixelMap类型给对端设备设置媒体信息。

**类型：** image.PixelMap \| string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-mediaImage?: image.PixelMap | string--><!--Device-AVMediaDescription-mediaImage?: image.PixelMap | string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## mediaSize

```TypeScript
mediaSize?: int
```

播放列表媒体的大小。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-mediaSize?: int--><!--Device-AVMediaDescription-mediaSize?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## mediaType

```TypeScript
mediaType?: string
```

播放列表媒体类型。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-mediaType?: string--><!--Device-AVMediaDescription-mediaType?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## mediaUri

```TypeScript
mediaUri?: string
```

播放列表媒体URI。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-mediaUri?: string--><!--Device-AVMediaDescription-mediaUri?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## pcmSrc

```TypeScript
pcmSrc?: boolean
```

播放列表是否使用PCM数据源。true表示使用PCM数据源，false表示不使用PCM数据源。

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-pcmSrc?: boolean--><!--Device-AVMediaDescription-pcmSrc?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## startPosition

```TypeScript
startPosition?: int
```

播放列表媒体起始播放位置。音视频投播场景中，在投播直播资源时，此字段应置空或赋值为0。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-startPosition?: int--><!--Device-AVMediaDescription-startPosition?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## subtitle

```TypeScript
subtitle?: string
```

子标题。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-subtitle?: string--><!--Device-AVMediaDescription-subtitle?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## title

```TypeScript
title?: string
```

标题。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVMediaDescription-title?: string--><!--Device-AVMediaDescription-title?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

