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

## enablePredicate

```TypeScript
enablePredicate?: boolean
```

Indicates the table-level synchronization switch.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CloudSyncConfig-enablePredicate?: boolean--><!--Device-CloudSyncConfig-enablePredicate?: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

## mode

```TypeScript
mode: SyncMode
```

Indicates the database synchronization mode.

**Type:** [SyncMode](arkts-arkdata-relationalstore-syncmode-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CloudSyncConfig-mode: SyncMode--><!--Device-CloudSyncConfig-mode: SyncMode-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

## predicate

```TypeScript
predicate?: RdbPredicates
```

Indicates the table-level synchronization predicate.

**Type:** [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CloudSyncConfig-predicate?: RdbPredicates--><!--Device-CloudSyncConfig-predicate?: RdbPredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client
