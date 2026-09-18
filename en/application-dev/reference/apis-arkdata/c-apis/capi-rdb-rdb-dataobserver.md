# Rdb_DataObserver

```c
typedef struct Rdb_DataObserver {...} Rdb_DataObserver
```

## Overview

Indicates the observer of data.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void *context | The context of data observer. |
| [Rdb_SubscribeCallback](capi-rdb-rdb-subscribecallback.md) callback | The callback of data observer. |


