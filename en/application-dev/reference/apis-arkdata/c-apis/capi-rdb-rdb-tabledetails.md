# Rdb_TableDetails

```c
typedef struct Rdb_TableDetails {...} Rdb_TableDetails
```

## Overview

Describes the {@link Rdb_Statistic} details of the table.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char *table | Indicates the name of changed table. |
| [Rdb_Statistic](capi-rdb-rdb-statistic.md) upload | Describes the {@link Rdb_Statistic} details of the upload process. |
| [Rdb_Statistic](capi-rdb-rdb-statistic.md) download | Describes the {@link Rdb_Statistic} details of the download process. |


