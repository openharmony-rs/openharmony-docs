# Rdb_ProgressDetails

```c
typedef struct Rdb_ProgressDetails {...} Rdb_ProgressDetails
```

## Overview

Describes detail of the cloud sync progress.

<!--Device-struct Rdb_ProgressDetails {...}--><!--Device-struct Rdb_ProgressDetails {...}-End-->

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Related module**: [RDB](capi-arkdata-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int version | The version used to uniquely identify the Rdb_ProgressDetails struct.<br><!--Device-int version--><!--Device-int version-End--> |
| int schedule | Describes the status of data sync progress. Defined in [Rdb_Progress](capi-relational-store-h.md#rdb_progress).<br><!--Device-int schedule--><!--Device-int schedule-End--> |
| int code | Describes the code of data sync progress. Defined in [Rdb_ProgressCode](capi-relational-store-h.md#rdb_progresscode).<br><!--Device-int code--><!--Device-int code-End--> |
| int32_t tableLength | Describes the length of changed tables in data sync progress.<br><!--Device-int32_t tableLength--><!--Device-int32_t tableLength-End--> |


