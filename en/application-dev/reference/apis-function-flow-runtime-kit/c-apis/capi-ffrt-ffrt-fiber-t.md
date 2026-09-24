# ffrt_fiber_t

```c
typedef struct ffrt_fiber_t {...} ffrt_fiber_t
```

## Overview

Defines the fiber structure used to store fiber execution context.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 20

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uintptr_t storage[ffrt_fiber_storage_size] | Internal storage backing the fiber execution context. Do not access directly; use {@link ffrt_fiber_init} to initialize and {@link ffrt_fiber_switch} to switch. |


