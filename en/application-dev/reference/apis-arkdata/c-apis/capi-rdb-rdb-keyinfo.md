# Rdb_KeyInfo

```c
typedef struct Rdb_KeyInfo {...} Rdb_KeyInfo
```

## Overview

Describes the primary keys or row-ids of changed rows.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int count | Indicates the count of the primary keys or row-ids. |
| int type | Indicates data type {@link OH_ColumnType} of the key. |
| union Rdb_KeyData | Indicates the data of the key info. |
| uint64_t integer | Indicates uint64_t type of the data. |
| double real | Indicates double type of the data. |
| const char *text;
 } *data | Indicates const char * type of the data. |


