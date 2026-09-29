# Statistic

```TypeScript
interface Statistic
```

Defines a struct for the device-cloud sync statistics of a database table.

**Since:** 10

<!--Device-relationalStore-interface Statistic--><!--Device-relationalStore-interface Statistic-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## failed

```TypeScript
failed: number
```

Number of rows that failed to be synced between the device and cloud in the database table.

**Type:** number

**Since:** 10

<!--Device-Statistic-failed: int--><!--Device-Statistic-failed: int-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## remained

```TypeScript
remained: number
```

Number of rows that are not executed for device-cloud sync in the database table.

**Type:** number

**Since:** 10

<!--Device-Statistic-remained: int--><!--Device-Statistic-remained: int-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## successful

```TypeScript
successful: number
```

Number of rows that are successfully synced between the device and cloud in the database table.

**Type:** number

**Since:** 10

<!--Device-Statistic-successful: int--><!--Device-Statistic-successful: int-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## total

```TypeScript
total: number
```

Total number of rows to be synced between the device and cloud in the database table.

**Type:** number

**Since:** 10

<!--Device-Statistic-total: int--><!--Device-Statistic-total: int-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
