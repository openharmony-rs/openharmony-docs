# CloudSyncConfig

```TypeScript
interface CloudSyncConfig
```

Cloud sync configuration.

**Since:** 26.0.0

<!--Device-relationalStore-interface CloudSyncConfig--><!--Device-relationalStore-interface CloudSyncConfig-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## downloadOnly

```TypeScript
downloadOnly?: boolean
```

Indicates whether the sync operation should be download‑only.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CloudSyncConfig-downloadOnly?: boolean--><!--Device-CloudSyncConfig-downloadOnly?: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## fullSync

```TypeScript
fullSync?: boolean
```

Specifies whether to perform full synchronization. When set to true, all data is synchronizd from the cloud to the local device. When set to false (default), only incremental changes since the last synchronization are applied. Default value: false.

**Type:** boolean

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CloudSyncConfig-fullSync?: boolean--><!--Device-CloudSyncConfig-fullSync?: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.
