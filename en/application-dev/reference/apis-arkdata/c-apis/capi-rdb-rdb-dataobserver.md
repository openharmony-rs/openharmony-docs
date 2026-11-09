# Rdb_DataObserver

```c
struct Rdb_DataObserver {...}
```

## Overview

Indicates the observer of data.

<!--Device-struct Rdb_DataObserver {...}--><!--Device-struct Rdb_DataObserver {...}-End-->

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Related module**: [RDB](capi-arkdata-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void *context | The context of data observer. |
| [Rdb_SubscribeCallback](capi-rdb-rdb-subscribecallback.md) callback | The callback of data observer. |


