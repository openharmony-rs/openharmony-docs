# Audio

```TypeScript
class Audio extends File
```

Audio data, a subclass of [File](arkts-arkdata-unifieddatachannel-file-c.md), used to describe an audio file.

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

URI of the local audio data or network audio data. The URI of the local audio data can be obtained by calling [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md).

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Audio-get audioUri(): string--><!--Device-Audio-get audioUri(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set audioUri(value: string)
```

URI of the local audio data or network audio data. The URI of the local audio data can be obtained by calling [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md).

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Audio-set audioUri(value: string)--><!--Device-Audio-set audioUri(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
