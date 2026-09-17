# Rdb_ProgressDetails

```c
typedef struct Rdb_ProgressDetails {...} Rdb_ProgressDetails
```

## Overview

Describes detail of the cloud sync progress.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int version | The version used to uniquely identify the Rdb_ProgressDetails struct. |
| int schedule | Describes the status of data sync progress. Defined in [Rdb_Progress](capi-relational-store-h.md#rdb_progress). |
| int code | Describes the code of data sync progress. Defined in {@link Rdb_ProgressCode}. |
| int32_t tableLength | Describes the length of changed tables in data sync progress. |


