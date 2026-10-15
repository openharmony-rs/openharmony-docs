# Rdb_KeyInfo

```c
struct Rdb_KeyInfo {...}
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
| int count | Indicates the count of the primary keys or row-ids. |
| int type | Indicates data type [OH_ColumnType](capi-oh-data-value-h.md#oh_columntype) of the key. |
| data.integer | Indicates uint64_t type of the data. |
| data.real | Indicates double type of the data. |
| data->text | Indicates const char * type of the data. |


