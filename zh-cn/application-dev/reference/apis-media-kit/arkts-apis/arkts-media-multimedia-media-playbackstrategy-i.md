# PlaybackStrategy

Provides preferred playback settings for player.

**起始版本：** 23

<!--Device-unnamed-interface PlaybackStrategy--><!--Device-unnamed-interface PlaybackStrategy-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## enableSuperResolution

```TypeScript
enableSuperResolution?: boolean
```

Enable super-resolution feature. default is false. Must enable super-resolution feature before calling setSuperResolution and setVideoWindowSize.

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlaybackStrategy-enableSuperResolution?: boolean--><!--Device-PlaybackStrategy-enableSuperResolution?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## keepDecodingOnMute

```TypeScript
keepDecodingOnMute?: boolean
```

Indicates whether to keep the decoder working when closing the media, which is used to facilitate quick opening of the media. Currently only supports video

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlaybackStrategy-keepDecodingOnMute?: boolean--><!--Device-PlaybackStrategy-keepDecodingOnMute?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## mutedMediaType

```TypeScript
mutedMediaType?: MediaType
```

mute the specified media stream when playing.

**类型：** [MediaType](arkts-media-multimedia-media-mediatype-e.md)

**起始版本：** 23

<!--Device-PlaybackStrategy-mutedMediaType?: MediaType--><!--Device-PlaybackStrategy-mutedMediaType?: MediaType-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredAudioLanguage

```TypeScript
preferredAudioLanguage?: string
```

Audio language.

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlaybackStrategy-preferredAudioLanguage?: string--><!--Device-PlaybackStrategy-preferredAudioLanguage?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredBufferDuration

```TypeScript
preferredBufferDuration?: int
```

Chooses a preferred buffer duration. &lt;p&gt;The preferred buffer duration in the playback policy, is used to set the buffer size. For details, see Online Video Frame Freezing Optimization Practice.&lt;/p&gt;

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlaybackStrategy-preferredBufferDuration?: int--><!--Device-PlaybackStrategy-preferredBufferDuration?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredBufferDurationForPlaying

```TypeScript
preferredBufferDurationForPlaying?: double
```

Customize the buffering threshold for start or restart playing. The unit is second.

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlaybackStrategy-preferredBufferDurationForPlaying?: double--><!--Device-PlaybackStrategy-preferredBufferDurationForPlaying?: double-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredHdr

```TypeScript
preferredHdr?: boolean
```

If true, the player should choose HDR stream if exist.

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlaybackStrategy-preferredHdr?: boolean--><!--Device-PlaybackStrategy-preferredHdr?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredHeight

```TypeScript
preferredHeight?: int
```

Choose a stream with height close to it.

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlaybackStrategy-preferredHeight?: int--><!--Device-PlaybackStrategy-preferredHeight?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredSubtitleLanguage

```TypeScript
preferredSubtitleLanguage?: string
```

Subtitle language.

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlaybackStrategy-preferredSubtitleLanguage?: string--><!--Device-PlaybackStrategy-preferredSubtitleLanguage?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## preferredWidth

```TypeScript
preferredWidth?: int
```

Choose a stream with width close to it.

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlaybackStrategy-preferredWidth?: int--><!--Device-PlaybackStrategy-preferredWidth?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## showFirstFrameOnPrepare

```TypeScript
showFirstFrameOnPrepare?: boolean
```

Show first frame on prepare.

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlaybackStrategy-showFirstFrameOnPrepare?: boolean--><!--Device-PlaybackStrategy-showFirstFrameOnPrepare?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## thresholdForAutoQuickPlay

```TypeScript
thresholdForAutoQuickPlay?: double
```

set max buffering threshold for liveStreaming or avplayer while change the speed. It is recommended that the value be 2 seconds greater than the starting waterline.

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PlaybackStrategy-thresholdForAutoQuickPlay?: double--><!--Device-PlaybackStrategy-thresholdForAutoQuickPlay?: double-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

