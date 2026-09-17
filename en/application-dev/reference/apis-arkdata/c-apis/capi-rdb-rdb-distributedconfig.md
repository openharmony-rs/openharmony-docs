# Rdb_DistributedConfig

```c
typedef struct Rdb_DistributedConfig {...} Rdb_DistributedConfig
```

## Overview

Manages the distributed configuration of the table.

**Since**: 11

**Related module**: [RDB](capi-rdb.md)

**Header file**: [relational_store.h](capi-relational-store-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int version | The version used to uniquely identify the Rdb_DistributedConfig struct. |
| bool isAutoSync | Specifies whether the table auto syncs. |


