# Rdb_ProgressObserver

```c
typedef struct Rdb_ProgressObserver {...} Rdb_ProgressObserver
```

## Overview

The observer of progress.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void *context | The context of progress observer. |
| [Rdb_ProgressCallback](capi-relational-store-h.md#rdb_progresscallback) callback | The callback function of progress observer. |


