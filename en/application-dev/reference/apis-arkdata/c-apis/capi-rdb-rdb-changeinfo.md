# Rdb_ChangeInfo

```c
typedef struct Rdb_ChangeInfo {...} Rdb_ChangeInfo
```

## Overview

Describes the notify info of data change.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int version | The version used to uniquely identify the Rdb_ChangeInfo struct. |
| const char *tableName | The name of changed table. |
| int ChangeType | The {@link Rdb_ChangeType} of changed table. |
| [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) inserted | The {@link Rdb_KeyInfo} of inserted rows. |
| [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) updated | The {@link Rdb_KeyInfo} of updated rows. |
| [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) deleted | The {@link Rdb_KeyInfo} of deleted rows. |


