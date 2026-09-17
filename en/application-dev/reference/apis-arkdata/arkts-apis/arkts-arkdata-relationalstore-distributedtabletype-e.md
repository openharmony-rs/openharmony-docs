# DistributedTableType

Enumerates the distributed table types. Use the enum name rather than the enum value. This item is a database-level configuration. If a database contains multiple distributed tables, all tables must use the same distributed table type; switching the table type or upgrade tables is not supported.

**Since:** 23

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## DEVICE_COLLABORATION

```TypeScript
DEVICE_COLLABORATION = 0
```

Multi-device collaboration table. Data on each device is stored in an independent distributed table in an isolated manner instead of being written to the local table. The name of the distributed table is formed by prepending the peer device's device ID to the original table name.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## SINGLE_VERSION

```TypeScript
SINGLE_VERSION = 1
```

Single version table. Data is directly written to the local table of the peer device through the distributed data management framework.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
