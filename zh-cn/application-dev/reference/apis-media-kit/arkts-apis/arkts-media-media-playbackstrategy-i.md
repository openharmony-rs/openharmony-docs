# PlaybackStrategy

播放器首选播放设置。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## enableSuperResolution

```TypeScript
enableSuperResolution?: boolean
```

是否启用超分。默认是关闭的。 在调用之前必须启用超分辨率功能 [setSuperResolution](arkts-media-media-avplayer-i.md#setsuperresolution) 和 [setVideoWindowSize](arkts-media-media-avplayer-i.md#setvideowindowsize).

**类型：** boolean

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## keepDecodingOnMute

```TypeScript
keepDecodingOnMute?: boolean
```

在关闭媒体时是否保持解码器工作，用于方便快速打开媒体。目前仅支持视频。

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## mutedMediaType

```TypeScript
mutedMediaType?: MediaType
```

播放时静音指定的媒体流。

**类型：** MediaType

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredAudioLanguage

```TypeScript
preferredAudioLanguage?: string
```

音频语言。

**类型：** string

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredBufferDuration

```TypeScript
preferredBufferDuration?: number
```

选择缓冲时长。<p>The preferred buffer duration in the playback policy, is used to set the buffer size. For details, see Online Video Frame Freezing Optimization Practice.</p>

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredBufferDurationForPlaying

```TypeScript
preferredBufferDurationForPlaying?: number
```

自定义开始或重新播放的缓冲阈值，单位为秒。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredHdr

```TypeScript
preferredHdr?: boolean
```

如果是，应该选择HDR流（如果有的话）。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredHeight

```TypeScript
preferredHeight?: number
```

选择高度接近的流。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredSubtitleLanguage

```TypeScript
preferredSubtitleLanguage?: string
```

字幕语言。

**类型：** string

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredWidth

```TypeScript
preferredWidth?: number
```

选择宽度接近的流。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## showFirstFrameOnPrepare

```TypeScript
showFirstFrameOnPrepare?: boolean
```

prepare时显示首帧。

**类型：** boolean

**起始版本：** 17

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## thresholdForAutoQuickPlay

```TypeScript
thresholdForAutoQuickPlay?: number
```

在更改速度时，为直播或 AVPlayer 设置最大缓冲阈值。 建议比起始水位高出2秒。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core
