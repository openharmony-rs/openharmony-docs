# BackupConfig

```TypeScript
interface BackupConfig
```

Configures database backup.

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

Name of the database to back up. There is no length limit, but the name cannot contain slashes (/).

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupConfig-fileName: string--><!--Device-BackupConfig-fileName: string-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## filePath

```TypeScript
filePath: string
```

Path of the database to back up. There is no length limit.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupConfig-filePath: string--><!--Device-BackupConfig-filePath: string-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore
