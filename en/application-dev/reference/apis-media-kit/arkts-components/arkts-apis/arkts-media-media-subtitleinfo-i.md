# SubtitleInfo

```TypeScript
interface SubtitleInfo
```

Provides subtitle information. When a subtitle update event is subscribed to, the information about the external subtitle is returned through a callback. Can be synchronized to the time reported by AVPlayer#timeUpdate event

**Since:** 12

<!--Device-media-interface SubtitleInfo--><!--Device-media-interface SubtitleInfo-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## duration

```TypeScript
duration?: number
```

Duration of the text to be displayed, as milliseconds.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SubtitleInfo-duration?: int--><!--Device-SubtitleInfo-duration?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## startTime

```TypeScript
startTime?: number
```

Display start time of the text, as milliseconds.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SubtitleInfo-startTime?: int--><!--Device-SubtitleInfo-startTime?: int-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## text

```TypeScript
text?: string
```

Text information of current update event.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SubtitleInfo-text?: string--><!--Device-SubtitleInfo-text?: string-End-->

**System capability:** SystemCapability.Multimedia.Media.Core
