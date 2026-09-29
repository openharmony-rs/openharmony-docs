# Rdb_KeyInfo

```c
union Rdb_KeyInfo {...}
```

## Overview

Describes the primary keys or row-ids of changed rows.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t integer | Indicates uint64_t type of the data. |
| double real | Indicates double type of the data. |
| const char *text;
 } *data | Indicates const char * type of the data. |


