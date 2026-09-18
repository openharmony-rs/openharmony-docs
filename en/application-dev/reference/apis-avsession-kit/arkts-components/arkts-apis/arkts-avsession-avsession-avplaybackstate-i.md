# AVPlaybackState

Used to indicate the playback state of the current media. If the playback state of the media changes, it needs to be updated synchronously

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## activeItemId

```TypeScript
activeItemId?: number
```

Current active item id

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## bufferedTime

```TypeScript
bufferedTime?: number
```

The current buffered time, the maximum playable position, described by milliseconds.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## duration

```TypeScript
duration?: number
```

The duration of this media asset, described by milliseconds.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

## extras

```TypeScript
extras?: {[key: string]: Object}
```

Current custom media packets

**Type:** {[key: string]: Object}

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## isFavorite

```TypeScript
isFavorite?: boolean
```

Current Favorite Status

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## loopMode

```TypeScript
loopMode?: LoopMode
```

Current playback loop mode. See [LoopMode](arkts-avsession-avsession-loopmode-e.md)

**Type:** [LoopMode](arkts-avsession-avsession-loopmode-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## maxVolume

```TypeScript
maxVolume?: number
```

maximum volume

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## muted

```TypeScript
muted?: boolean
```

Current muted status

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## position

```TypeScript
position?: PlaybackPosition
```

Current playback position of this media. See [PlaybackPosition](arkts-avsession-avsession-playbackposition-i.md)

**Type:** [PlaybackPosition](arkts-avsession-avsession-playbackposition-i.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## speed

```TypeScript
speed?: number
```

Current playback speed

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## state

```TypeScript
state?: PlaybackState
```

Current playback state. See [PlaybackState](arkts-avsession-avsession-playbackstate-e.md)

**Type:** [PlaybackState](arkts-avsession-avsession-playbackstate-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## videoHeight

```TypeScript
videoHeight?: number
```

The video height of this media asset.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## videoWidth

```TypeScript
videoWidth?: number
```

The video width of this media asset.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

## volume

```TypeScript
volume?: number
```

Current player volume

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core
