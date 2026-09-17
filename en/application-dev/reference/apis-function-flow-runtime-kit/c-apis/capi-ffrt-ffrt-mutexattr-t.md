# ffrt_mutexattr_t

```c
typedef struct ffrt_mutexattr_t {...} ffrt_mutexattr_t
```

## Overview

Defines the mutex attribute structure used to store mutex attribute information.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| long storage | Internal storage backing the mutex attribute. Do not access directly; use {@link ffrt_mutexattr_init} to initialize. |


