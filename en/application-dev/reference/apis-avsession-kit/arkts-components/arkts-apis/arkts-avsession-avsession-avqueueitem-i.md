# AVQueueItem

```TypeScript
interface AVQueueItem
```

The item in the playlist of the session

**Since:** 10

<!--Device-avSession-interface AVQueueItem--><!--Device-avSession-interface AVQueueItem-End-->

**System capability:** SystemCapability.Multimedia.AVSession.Core

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## description

```TypeScript
description?: AVMediaDescription
```

The media description of the item in the playlist.

**Type:** [AVMediaDescription](arkts-avsession-avsession-avmediadescription-i.md)

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AVQueueItem-description?: AVMediaDescription--><!--Device-AVQueueItem-description?: AVMediaDescription-End-->

**System capability:** SystemCapability.Multimedia.AVSession.Core

## itemId

```TypeScript
itemId: number
```

Sequence number of the item in the playlist.

**Type:** number

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AVQueueItem-itemId: int--><!--Device-AVQueueItem-itemId: int-End-->

**System capability:** SystemCapability.Multimedia.AVSession.Core
