# HAMode (System API)

```TypeScript
enum HAMode
```

Enumerates the high availability modes of the RDB store.

**Since:** 12

<!--Device-relationalStore-enum HAMode--><!--Device-relationalStore-enum HAMode-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.

## SINGLE

```TypeScript
SINGLE = 0
```

SINGLE: Data is written to a single RDB store.

**Since:** 12

<!--Device-HAMode-SINGLE = 0--><!--Device-HAMode-SINGLE = 0-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.

## MAIN_REPLICA

```TypeScript
MAIN_REPLICA = 1
```

MAIN_REPLICA: Data is written to the main and replica RDB stores.

**Since:** 12

<!--Device-HAMode-MAIN_REPLICA = 1--><!--Device-HAMode-MAIN_REPLICA = 1-End-->

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.
