# Rdb_SubscribeCallback

```c
typedef union Rdb_SubscribeCallback {...} Rdb_SubscribeCallback
```

## Overview

Indicates the callback functions.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Rdb_DetailsObserver](capi-relational-store-h.md#rdb_detailsobserver) detailsObserver | The callback function of cloud data change details event. |
| [Rdb_BriefObserver](capi-relational-store-h.md#rdb_briefobserver) briefObserver | The callback function of cloud data change event. |


