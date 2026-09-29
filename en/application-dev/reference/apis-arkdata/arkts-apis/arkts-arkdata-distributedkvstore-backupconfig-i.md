# BackupConfig

```TypeScript
interface BackupConfig
```

Provides backup config to backup or restore KVStore.

**Since:** 24

<!--Device-distributedKVStore-interface BackupConfig--><!--Device-distributedKVStore-interface BackupConfig-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## Modules to Import

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## fileName

```TypeScript
fileName: string
```

Specifies the file name to the backup database

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupConfig-fileName: string--><!--Device-BackupConfig-fileName: string-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## filePath

```TypeScript
filePath: string
```

Specifies the root directory relative to the backup database

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupConfig-filePath: string--><!--Device-BackupConfig-filePath: string-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore
