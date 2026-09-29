# ffrt_queue_attr_t

```c
typedef struct ffrt_queue_attr_t {...} ffrt_queue_attr_t
```

## Overview

Defines the queue attribute structure used to store queue attribute information.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t storage[(ffrt_queue_attr_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)] | Internal storage backing the queue attribute. Do not access directly; use the ffrt_queue_attr_init and `ffrt_queue_attr_set_*` APIs to manage contents. |


