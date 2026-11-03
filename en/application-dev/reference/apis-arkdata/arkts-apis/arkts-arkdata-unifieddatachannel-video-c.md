# Video

```TypeScript
class Video extends File
```

Video data, a subclass of [File](arkts-arkdata-unifieddatachannel-file-c.md), used to describe a video file.

**Inheritance/Implementation:** Video extends [File](arkts-arkdata-unifieddatachannel-file-c.md)

**Since:** 10

<!--Device-unifiedDataChannel-class Video extends File--><!--Device-unifiedDataChannel-class Video extends File-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## videoUri

```TypeScript
get videoUri(): string
```

URI of the local video data or network video. The URI of the local video data can be obtained by calling [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md).

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Video-get videoUri(): string--><!--Device-Video-get videoUri(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set videoUri(value: string)
```

URI of the local video data or network video. The URI of the local video data can be obtained by calling [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md).

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Video-set videoUri(value: string)--><!--Device-Video-set videoUri(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
