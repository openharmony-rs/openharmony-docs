# SyncInfo (System API)

```TypeScript
interface SyncInfo
```

Represents information about the last device-cloud sync.

**Since:** 12

<!--Device-cloudData-interface SyncInfo--><!--Device-cloudData-interface SyncInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## code

```TypeScript
code: relationalStore.ProgressCode
```

Result of the last device-cloud sync.

**Type:** [relationalStore.ProgressCode](arkts-arkdata-relationalstore-progresscode-e.md)

**Since:** 12

<!--Device-SyncInfo-code: relationalStore.ProgressCode--><!--Device-SyncInfo-code: relationalStore.ProgressCode-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## finishTime

```TypeScript
finishTime: Date
```

End time of the last device-cloud sync.

**Type:** Date

**Since:** 12

<!--Device-SyncInfo-finishTime: Date--><!--Device-SyncInfo-finishTime: Date-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## startTime

```TypeScript
startTime: Date
```

Start time of the last device-cloud sync.

**Type:** Date

**Since:** 12

<!--Device-SyncInfo-startTime: Date--><!--Device-SyncInfo-startTime: Date-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## syncStatus

```TypeScript
syncStatus?: SyncStatus
```

Status of the last device-cloud sync. The default value is **cloudData.SyncStatus.RUNNING**.

**Type:** [SyncStatus](arkts-arkdata-clouddata-syncstatus-e-sys.md)

**Since:** 18

<!--Device-SyncInfo-syncStatus?: SyncStatus--><!--Device-SyncInfo-syncStatus?: SyncStatus-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.
