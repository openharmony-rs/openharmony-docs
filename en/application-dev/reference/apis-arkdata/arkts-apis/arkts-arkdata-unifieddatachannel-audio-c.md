# Audio

```TypeScript
class Audio extends File
```

Represents audio data. It is a child class of [File](arkts-arkdata-unifieddatachannel-file-c.md) and is used to describe an audio file.

**Inheritance/Implementation:** Audio extends [File](arkts-arkdata-unifieddatachannel-file-c.md)

**Since:** 10

<!--Device-unifiedDataChannel-class Audio extends File--><!--Device-unifiedDataChannel-class Audio extends File-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## audioUri

```TypeScript
get audioUri(): string
```

Indicates the uri of audio

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Audio-get audioUri(): string--><!--Device-Audio-get audioUri(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set audioUri(value: string)
```

Indicates the uri of audio

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Audio-set audioUri(value: string)--><!--Device-Audio-set audioUri(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
