# AVQueueInfo (System API)

The play list information definition.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## avQueueId

```TypeScript
avQueueId: string
```

The id of play list

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

**System API:** This is a system API.

## avQueueImage

```TypeScript
avQueueImage: image.PixelMap | string
```

The artwork of play list, can be a PixelMap or a URI formatted string,

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) &#124; string

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

**System API:** This is a system API.

## avQueueName

```TypeScript
avQueueName: string
```

The name of play list

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

The bundle name of application which current play list belongs to.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

**System API:** This is a system API.

## lastPlayedTime

```TypeScript
lastPlayedTime?: number
```

The time when the user last played the playlist. The time format can be system, such as 1611081385000, it means 2021-01-20 02:36:25.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

**System API:** This is a system API.
