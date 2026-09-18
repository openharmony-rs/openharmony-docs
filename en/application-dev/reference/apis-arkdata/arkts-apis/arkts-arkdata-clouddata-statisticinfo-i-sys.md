# StatisticInfo (System API)

Represents the device-cloud sync statistics.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## inserted

```TypeScript
inserted: number
```

Number of data records that are added locally and have not been synced to the cloud. For example, the value **2** indicates that the table has two data records that are added locally but not synced to the cloud.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## normal

```TypeScript
normal: number
```

Number of consistent data records between the device and the cloud. For example, the value **2** indicates that table has two data records that are consistent between the device and the cloud.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## table

```TypeScript
table: string
```

Name of the table queried. For example, the value **cloud_notes** indicates that the sync information of the **cloud_notes** table is queried.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.

## updated

```TypeScript
updated: number
```

Number of data records that are modified locally or on the cloud but have not been synced. For example, the value **2** indicates that the table has two data records that are updated locally or on the cloud but not synced.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Config

**System API:** This is a system API.
