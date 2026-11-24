# Rdb_SubscribeCallback

```c
typedef union Rdb_SubscribeCallback {...} Rdb_SubscribeCallback
```

## Overview

Indicates the callback functions.

<!--Device-union Rdb_SubscribeCallback {...}--><!--Device-union Rdb_SubscribeCallback {...}-End-->

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Related module**: [RDB](capi-arkdata-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Rdb_DetailsObserver](capi-relational-store-h.md#rdb_detailsobserver) detailsObserver | The callback function of cloud data change details event.<br><!--Device-Rdb_DetailsObserver detailsObserver--><!--Device-Rdb_DetailsObserver detailsObserver-End--> |
| [Rdb_BriefObserver](capi-relational-store-h.md#rdb_briefobserver) briefObserver | The callback function of cloud data change event.<br><!--Device-Rdb_BriefObserver briefObserver--><!--Device-Rdb_BriefObserver briefObserver-End--> |


