# Rdb_Statistic

```c
typedef struct Rdb_Statistic {...} Rdb_Statistic
```

## Overview

Describes the statistic of the cloud sync process.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int total | Describes the total number of data to sync. |
| int successful | Describes the number of successfully synced data. |
| int failed | Describes the number of data failed to sync. |
| int remained | Describes the number of data remained to sync. |


