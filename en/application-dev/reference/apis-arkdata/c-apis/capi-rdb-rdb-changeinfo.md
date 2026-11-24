# Rdb_ChangeInfo

```c
typedef struct Rdb_ChangeInfo {...} Rdb_ChangeInfo
```

## Overview

Describes the notify info of data change.

<!--Device-struct Rdb_ChangeInfo {...}--><!--Device-struct Rdb_ChangeInfo {...}-End-->

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Related module**: [RDB](capi-arkdata-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int version | The version used to uniquely identify the Rdb_ChangeInfo struct.<br><!--Device-int version--><!--Device-int version-End--> |
| const char *tableName | The name of changed table.<br><!--Device-const char *tableName--><!--Device-const char *tableName-End--> |
| int ChangeType | The [Rdb_ChangeType](capi-relational-store-h.md#rdb_changetype) of changed table.<br><!--Device-int ChangeType--><!--Device-int ChangeType-End--> |
| [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) inserted | The [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) of inserted rows.<br><!--Device-Rdb_KeyInfo inserted--><!--Device-Rdb_KeyInfo inserted-End--> |
| [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) updated | The [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) of updated rows.<br><!--Device-Rdb_KeyInfo updated--><!--Device-Rdb_KeyInfo updated-End--> |
| [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) deleted | The [Rdb_KeyInfo](capi-rdb-rdb-keyinfo.md) of deleted rows.<br><!--Device-Rdb_KeyInfo deleted--><!--Device-Rdb_KeyInfo deleted-End--> |


