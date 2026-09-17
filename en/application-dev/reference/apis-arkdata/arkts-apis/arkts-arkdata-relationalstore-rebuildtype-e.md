# RebuildType

Enumerates the RDB store rebuild types. Use the enum name rather than the enum value.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## NONE

```TypeScript
NONE = 0
```

The RDB store is not rebuilt.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## REBUILT

```TypeScript
REBUILT = 1
```

The RDB store is rebuilt and creates an empty database. You need to create tables and restore data.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## REPAIRED

```TypeScript
REPAIRED = 2
```

The database is repaired and the undamaged data is restored. Currently, only the [vector store](arkts-arkdata-relationalstore-storeconfig-i.md) supports this capability.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
