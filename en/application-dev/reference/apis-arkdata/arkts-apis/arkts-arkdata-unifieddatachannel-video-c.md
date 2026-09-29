# Video

```TypeScript
class Video extends File
```

Represents video data. It is a child class of [File](arkts-arkdata-unifieddatachannel-file-c.md) and is used to describe a video file.

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

Indicates the uri of video

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Video-get videoUri(): string--><!--Device-Video-get videoUri(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set videoUri(value: string)
```

Indicates the uri of video

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Video-set videoUri(value: string)--><!--Device-Video-set videoUri(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
