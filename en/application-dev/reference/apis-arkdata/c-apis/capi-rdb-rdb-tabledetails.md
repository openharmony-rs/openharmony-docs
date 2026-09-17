# Rdb_TableDetails

```c
typedef struct Rdb_TableDetails {...} Rdb_TableDetails
```

## Overview

Describes the [Rdb_Statistic](capi-rdb-rdb-statistic.md) details of the table.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char *table | Indicates the name of changed table. |
| [Rdb_Statistic](capi-rdb-rdb-statistic.md) upload | Describes the [Rdb_Statistic](capi-rdb-rdb-statistic.md) details of the upload process. |
| [Rdb_Statistic](capi-rdb-rdb-statistic.md) download | Describes the [Rdb_Statistic](capi-rdb-rdb-statistic.md) details of the download process. |


