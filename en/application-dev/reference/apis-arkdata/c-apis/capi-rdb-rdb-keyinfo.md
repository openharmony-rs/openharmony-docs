# Rdb_KeyInfo

```c
typedef struct Rdb_KeyInfo {...} Rdb_KeyInfo
```

## Overview

Describes the primary keys or row-ids of changed rows.

<!--Device-struct Rdb_KeyInfo {...}--><!--Device-struct Rdb_KeyInfo {...}-End-->

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Related module**: [RDB](capi-arkdata-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int count | Indicates the count of the primary keys or row-ids.<br><!--Device-int count--><!--Device-int count-End--> |
| int type | Indicates data type [OH_ColumnType](capi-oh-data-value-h.md#oh_columntype) of the key.<br><!--Device-int type--><!--Device-int type-End--> |
| data.integer | Indicates uint64_t type of the data.<br><!--Device-data.integer--><!--Device-data.integer-End--> |
| data.real | Indicates double type of the data.<br><!--Device-data.real--><!--Device-data.real-End--> |
| data.text | Indicates const char * type of the data.<br><!--Device-data.text--><!--Device-data.text-End--> |


