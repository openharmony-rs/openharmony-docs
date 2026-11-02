# Folder

```TypeScript
class Folder extends File
```

Folder type data, a subclass of [File](arkts-arkdata-unifieddatachannel-file-c.md), used to describe a folder.

**Inheritance/Implementation:** Folder extends [File](arkts-arkdata-unifieddatachannel-file-c.md)

**Since:** 10

<!--Device-unifiedDataChannel-class Folder extends File--><!--Device-unifiedDataChannel-class Folder extends File-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## folderUri

```TypeScript
get folderUri(): string
```

URI of a local folder or a network folder. The URI of a local folder can be obtained by [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md).

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Folder-get folderUri(): string--><!--Device-Folder-get folderUri(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set folderUri(value: string)
```

URI of a local folder or a network folder. The URI of a local folder can be obtained by [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md).

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Folder-set folderUri(value: string)--><!--Device-Folder-set folderUri(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
