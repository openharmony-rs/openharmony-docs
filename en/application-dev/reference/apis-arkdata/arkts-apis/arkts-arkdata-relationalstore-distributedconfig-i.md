# DistributedConfig

Defines a struct for distributed configuration of a table.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## assetConflictPolicy

```TypeScript
assetConflictPolicy?: AssetConflictPolicy
```

Specifies the asset conflict policy.

**Type:** [AssetConflictPolicy](arkts-arkdata-relationalstore-assetconflictpolicy-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## assetDownloadOnDemand

```TypeScript
assetDownloadOnDemand?: boolean
```

Specifies whether to download assets on demand.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## assetTempPath

```TypeScript
assetTempPath?: string
```

Specifies the asset temp path.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## asyncDownloadAsset

```TypeScript
asyncDownloadAsset?: boolean
```

Whether to download assets synchronously or asynchronously when device-cloud sync is being performed for the current RDB store. The value **true** means to use an asynchronous task to download assets after all data is downloaded; **false** means to download assets synchronously.

Default value: **false**.

**Type:** boolean

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## autoSync

```TypeScript
autoSync: boolean
```

Whether the table supports automatic device-cloud synchronization. If the value is **true**, the system can automatically trigger device-cloud sync. If the value is **false**, the system cannot automatically trigger device-cloud sync, and the [cloudSync] [cloudSync](arkts-arkdata-relationalstore-rdbstore-i.md#cloudsync) API needs to be called to trigger device-cloud sync.

**Type:** boolean

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## autoSyncSwitch

```TypeScript
autoSyncSwitch?: boolean
```

Specifies the auto synchronization switch.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## enableCloud

```TypeScript
enableCloud?: boolean
```

Whether to enable device-cloud sync for this RDB store. The value **true** means to enable device-cloud sync; **false** means the opposite. The default value is **true**.

**Type:** boolean

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## tableType

```TypeScript
tableType?: DistributedTableType
```

Distributed table type. **DEVICE_COLLABORATION** indicates the device collaboration table, and **SINGLE_VERSION** indicates the single version table. For cross-device data sync, the default value is **DEVICE_COLLABORATION**. For device-cloud data sync, the default value is **SINGLE_VERSION**, and **DEVICE_COLLABORATION** is not supported.

**Type:** [DistributedTableType](arkts-arkdata-relationalstore-distributedtabletype-e.md)

**Since:** 23

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
