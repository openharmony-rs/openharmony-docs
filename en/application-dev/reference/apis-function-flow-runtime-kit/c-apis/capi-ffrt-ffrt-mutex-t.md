# ffrt_mutex_t

```c
typedef struct ffrt_mutex_t {...} ffrt_mutex_t
```

## Overview

Defines the mutex structure used to store internal data of the mutex.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t storage[(ffrt_mutex_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)] | Internal storage backing the mutex. Do not access directly; use the `ffrt_mutex_*` APIs. |


