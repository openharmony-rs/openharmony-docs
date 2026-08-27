# AVTranscoderConfig

表示视频转码的参数设置。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## audioBitrate

```TypeScript
audioBitrate?: number
```

输出音频的码率，单位为比特率（bps），支持范围[1, 500000]。默认设置为48Kbps。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## audioCodec

```TypeScript
audioCodec?: CodecMimeType
```

输出音频的编码格式，当前仅支持AAC。默认设置为AAC。

**类型：** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## audioCodecV2

```TypeScript
audioCodecV2?: CodecMimeType
```

输出音频的编码格式。如果指定的编码格式不被支持，prepare会失败。默认设置为AAC。

**类型：** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## enableBFrame

```TypeScript
enableBFrame?: boolean
```

转码使能B帧编码。true表示开启B帧编码，默认为不开启B帧编码

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## fileFormat

```TypeScript
fileFormat: ContainerFormatType
```

输出视频文件的封装格式，当前视频文件仅支持MP4。

**类型：** [ContainerFormatType](arkts-media-media-containerformattype-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## videoBitrate

```TypeScript
videoBitrate?: number
```

输出视频的码率，单位为比特率（bps）。默认码率按输出视频的分辨率设置，[240p, 480P]默认码率值为1Mbps， (480P, 720P]默认码率值为2Mbps，(720P, 1080P]默认码率值为4Mbps，1080P及以上默认值为8Mbps。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## videoCodec

```TypeScript
videoCodec?: CodecMimeType
```

输出视频的编码格式，当前仅支持AVC和HEVC。若源视频编码格式为HEVC，则默认设置为HEVC，否则默认设置为AVC。

**类型：** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## videoFrameHeight

```TypeScript
videoFrameHeight?: number
```

输出视频帧的高，单位为像素（px），支持范围[240, 2160]。默认设置为源视频帧的高。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## videoFrameWidth

```TypeScript
videoFrameWidth?: number
```

输出视频帧的宽，单位为像素（px），支持范围[240, 3840]。默认设置为源视频帧的宽。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder
