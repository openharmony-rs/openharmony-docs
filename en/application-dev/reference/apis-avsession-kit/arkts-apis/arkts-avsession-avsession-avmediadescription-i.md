# AVMediaDescription

The description of the media for an item in the playlist of the session

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## albumCoverUri

```TypeScript
albumCoverUri?: string
```

The album cover uri of this media

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## albumTitle

```TypeScript
albumTitle?: string
```

The album title of this media

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## appName

```TypeScript
appName?: string
```

Application name.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## artist

```TypeScript
artist?: string
```

The artist of this media.

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

## creditsPosition

```TypeScript
creditsPosition?: number
```

Media credits position, described by milliseconds.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## dataSrc

```TypeScript
dataSrc?: media.AVDataSrcDescriptor
```

DataSource descriptor. The caller ensures the fileSize and callback are valid.

**Type:** [media.AVDataSrcDescriptor](../../apis-media-kit/arkts-apis/arkts-media-media-avdatasrcdescriptor-i.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.AVSession.Core

## description

```TypeScript
description?: string
```

The description of this media

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

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## drmScheme

```TypeScript
drmScheme?: string
```

The drm scheme supported by this resource which is represented by uuid.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Multimedia.AVSession.Core

## duration

```TypeScript
duration?: number
```

The duration of this media, described by milliseconds.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## extras

```TypeScript
extras?: {[key: string]: Object}
```

Any additional attributes that can be represented as key-value pairs

**Type:** {[key: string]: Object}

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

## fdSrc

```TypeScript
fdSrc?: media.AVFileDescriptor
```

Media file descriptor.

**Type:** [media.AVFileDescriptor](../../apis-media-kit/arkts-apis/arkts-media-media-avfiledescriptor-i.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## launchClientData

```TypeScript
launchClientData?: string
```

Custom data sent by the application to the receiver during casting.

**Type:** string

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## lyricContent

```TypeScript
lyricContent?: string
```

The lyric content of the media, it should be in standard lyric format

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## lyricUri

```TypeScript
lyricUri?: string
```

The lyric uri of the media.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## mediaImage

```TypeScript
mediaImage?: image.PixelMap | string
```

The image of this media asset displayed in the media center. It can be a PixelMap or a URI formatted string,

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) &#124; string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## mediaSize

```TypeScript
mediaSize?: number
```

The size of this media.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## mediaType

```TypeScript
mediaType?: string
```

The type of this media, such as video, audio and so on.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## mediaUri

```TypeScript
mediaUri?: string
```

The uri of the media, used to locate the media in some special cases

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## pcmSrc

```TypeScript
pcmSrc?: boolean
```

Source type that supports PCM casting. The application can send PCM data directly to the system through audio APIs, without using AVSession to set data.

**Type:** boolean

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## startPosition

```TypeScript
startPosition?: number
```

Media start position, described by milliseconds.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

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
