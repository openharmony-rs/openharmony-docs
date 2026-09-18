# AVMetadata

The metadata of the current media.Used to set the properties of the current media file

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## album

```TypeScript
album?: string
```

The album of this media

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## artist

```TypeScript
artist?: string
```

The artist of this media

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## assetId

```TypeScript
assetId: string
```

Unique ID used to represent this media.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## author

```TypeScript
author?: string
```

The author of this media

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## avQueueId

```TypeScript
avQueueId?: string
```

The id of play list which current media belongs to, it should be an unique identifier in the application.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

## avQueueImage

```TypeScript
avQueueImage?: image.PixelMap | string
```

The artwork of play list as a PixelMap or an uri formatted String,

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) &#124; string

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

## avQueueName

```TypeScript
avQueueName?: string
```

The name of play list which current media belongs to

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Multimedia.AVSession.Core

## bundleIcon

```TypeScript
readonly bundleIcon?: image.PixelMap
```

The image of the bundle icon as a PixelMap, no need to be set by application.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 18

**System capability:** SystemCapability.Multimedia.AVSession.Core

## composer

```TypeScript
composer?: string
```

The composer of this media

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

## description

```TypeScript
description?: string
```

The description of the media, used for display

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## displayTags

```TypeScript
displayTags?: number
```

The display tags supported by application to be displayed on media center

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

## drmSchemes

```TypeScript
drmSchemes?: Array<string>
```

The drm schemes supported by this session which are represented by uuid.

**Type:** Array&lt;string&gt;

**Since:** 12

**System capability:** SystemCapability.Multimedia.AVSession.Core

## duration

```TypeScript
duration?: number
```

The duration of this media, used to automatically calculate playback position, described by milliseconds.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## fastForwardSkipIntervals

```TypeScript
fastForwardSkipIntervals?: SkipIntervals
```

The supported skipIntervals when doing fast forward operation, the default is [SECONDS_15](arkts-avsession-avsession-skipintervals-e.md#seconds_15). The system will use this value for fastforward skip intervals instead of [skipIntervals](#skipintervals). If not set, the fast forward skip intervals still use [skipIntervals](#skipintervals). See [SkipIntervals](arkts-avsession-avsession-skipintervals-e.md)

**Type:** [SkipIntervals](arkts-avsession-avsession-skipintervals-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## filter

```TypeScript
filter?: number
```

The protocols supported by this session, if not set, the default is [TYPE_CAST_PLUS_STREAM](arkts-avsession-avsession-protocoltype-e.md#type_cast_plus_stream). See [ProtocolType](arkts-avsession-avsession-protocoltype-e.md)

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## lyric

```TypeScript
lyric?: string
```

The lyric of the media, it should be in standard lyric format

**Type:** string

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

## mediaImage

```TypeScript
mediaImage?: image.PixelMap | string
```

The image of the media as a PixelMap or an uri formatted String, used to display in media center.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) &#124; string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## nextAssetId

```TypeScript
nextAssetId?: string
```

The next playable media id. Used to tell the controller if there is a next playable media

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## previousAssetId

```TypeScript
previousAssetId?: string
```

The previous playable media id. Used to tell the controller if there is a previous playable media

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## publishDate

```TypeScript
publishDate?: Date
```

The publishDate of the media

**Type:** Date

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

## rewindSkipIntervals

```TypeScript
rewindSkipIntervals?: SkipIntervals
```

The supported skipIntervals when doing rewind operation, the default is [SECONDS_15](arkts-avsession-avsession-skipintervals-e.md#seconds_15). The system will use this value for rewind skip intervals instead of [skipIntervals](#skipintervals). If not set, the rewind skip intervals still use [skipIntervals](#skipintervals). See [SkipIntervals](arkts-avsession-avsession-skipintervals-e.md)

**Type:** [SkipIntervals](arkts-avsession-avsession-skipintervals-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## singleLyricText

```TypeScript
singleLyricText?: string
```

The single lyric text of the media, not including time prefix

**Type:** string

**Since:** 17

**Atomic service API:** This API can be used in atomic services since API version 17.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## skipIntervals

```TypeScript
skipIntervals?: SkipIntervals
```

The supported skipIntervals when doing fast forward and rewind operation, the default is [SECONDS_15](arkts-avsession-avsession-skipintervals-e.md#seconds_15). See [SkipIntervals](arkts-avsession-avsession-skipintervals-e.md)

**Type:** [SkipIntervals](arkts-avsession-avsession-skipintervals-e.md)

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

## subtitle

```TypeScript
subtitle?: string
```

The subtitle of the media, used for display

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## title

```TypeScript
title?: string
```

The title of this media, for display in media center.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## writer

```TypeScript
writer?: string
```

The writer of this media

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core
