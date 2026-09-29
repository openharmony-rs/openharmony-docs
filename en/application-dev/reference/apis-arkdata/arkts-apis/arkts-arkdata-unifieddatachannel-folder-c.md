# Folder

```TypeScript
class Folder extends File
```

Represents the folder data. It is a child class of [File](arkts-arkdata-unifieddatachannel-file-c.md) and is used to describe a folder.

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

Indicates the uri of folder

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Folder-get folderUri(): string--><!--Device-Folder-get folderUri(): string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set folderUri(value: string)
```

Indicates the uri of folder

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Folder-set folderUri(value: string)--><!--Device-Folder-set folderUri(value: string)-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
