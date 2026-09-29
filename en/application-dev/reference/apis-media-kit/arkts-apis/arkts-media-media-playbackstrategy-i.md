# PlaybackStrategy

```TypeScript
interface PlaybackStrategy
```

Provides preferred playback settings for player.

**Since:** 12

<!--Device-media-interface PlaybackStrategy--><!--Device-media-interface PlaybackStrategy-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## enableSuperResolution

```TypeScript
enableSuperResolution?: boolean
```

Enable super-resolution feature. default is false. Must enable super-resolution feature before calling [setSuperResolution](arkts-media-media-avplayer-i.md#setsuperresolution) and [setVideoWindowSize](arkts-media-media-avplayer-i.md#setvideowindowsize).

**Type:** boolean

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-PlaybackStrategy-enableSuperResolution?: boolean--><!--Device-PlaybackStrategy-enableSuperResolution?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## keepDecodingOnMute

```TypeScript
keepDecodingOnMute?: boolean
```

Indicates whether to keep the decoder working when closing the media, which is used to facilitate quick opening of the media. Currently only supports video

**Type:** boolean

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-PlaybackStrategy-keepDecodingOnMute?: boolean--><!--Device-PlaybackStrategy-keepDecodingOnMute?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## mutedMediaType

```TypeScript
mutedMediaType?: MediaType
```

mute the specified media stream when playing.

**Type:** [MediaType](arkts-media-media-mediatype-e.md)

**Since:** 12

<!--Device-PlaybackStrategy-mutedMediaType?: MediaType--><!--Device-PlaybackStrategy-mutedMediaType?: MediaType-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## preferredAudioLanguage

```TypeScript
preferredAudioLanguage?: string
```

Audio language.

**Type:** string

**Since:** 13

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 13.

<!--Device-PlaybackStrategy-preferredAudioLanguage?: string--><!--Device-PlaybackStrategy-preferredAudioLanguage?: string-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## preferredBufferDuration

```TypeScript
preferredBufferDuration?: number
```

Chooses a preferred buffer duration.

<p>The preferred buffer duration in the playback policy, is used to set the buffer size. For details, see Online Video Frame Freezing Optimization Practice.</p>

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PlaybackStrategy-preferredBufferDuration?: int--><!--Device-PlaybackStrategy-preferredBufferDuration?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## preferredBufferDurationForPlaying

```TypeScript
preferredBufferDurationForPlaying?: number
```

Customize the buffering threshold for start or restart playing. The unit is second.

**Type:** number

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-PlaybackStrategy-preferredBufferDurationForPlaying?: double--><!--Device-PlaybackStrategy-preferredBufferDurationForPlaying?: double-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## preferredHdr

```TypeScript
preferredHdr?: boolean
```

If true, the player should choose HDR stream if exist.

**Type:** boolean

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PlaybackStrategy-preferredHdr?: boolean--><!--Device-PlaybackStrategy-preferredHdr?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## preferredHeight

```TypeScript
preferredHeight?: number
```

Choose a stream with height close to it.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PlaybackStrategy-preferredHeight?: int--><!--Device-PlaybackStrategy-preferredHeight?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## preferredSubtitleLanguage

```TypeScript
preferredSubtitleLanguage?: string
```

Subtitle language.

**Type:** string

**Since:** 13

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 13.

<!--Device-PlaybackStrategy-preferredSubtitleLanguage?: string--><!--Device-PlaybackStrategy-preferredSubtitleLanguage?: string-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## preferredWidth

```TypeScript
preferredWidth?: number
```

Choose a stream with width close to it.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PlaybackStrategy-preferredWidth?: int--><!--Device-PlaybackStrategy-preferredWidth?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## showFirstFrameOnPrepare

```TypeScript
showFirstFrameOnPrepare?: boolean
```

Show first frame on prepare.

**Type:** boolean

**Since:** 17

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 17.

<!--Device-PlaybackStrategy-showFirstFrameOnPrepare?: boolean--><!--Device-PlaybackStrategy-showFirstFrameOnPrepare?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## thresholdForAutoQuickPlay

```TypeScript
thresholdForAutoQuickPlay?: number
```

set max buffering threshold for liveStreaming or avplayer while change the speed. It is recommended that the value be 2 seconds greater than the starting waterline.

**Type:** number

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-PlaybackStrategy-thresholdForAutoQuickPlay?: double--><!--Device-PlaybackStrategy-thresholdForAutoQuickPlay?: double-End-->

**System capability:** SystemCapability.Multimedia.Media.Core
