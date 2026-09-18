# Folder

Represents the folder data. It is a child class of [File](arkts-arkdata-unifieddatachannel-file-c.md) and is used to describe a folder.

**Inheritance/Implementation:** Folder extends [File](arkts-arkdata-unifieddatachannel-file-c.md)

**Since:** 10

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

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

```TypeScript
set folderUri(value: string)
```

Indicates the uri of folder

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
