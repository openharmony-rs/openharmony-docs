# ffrt_deps_t

```c
typedef struct ffrt_deps_t {...} ffrt_deps_t
```

## Overview

Defines the dependency structure, used to hold a list of dependencies for a task.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t len | Number of dependencies. |
| const [ffrt_dependence_t*](capi-ffrt-ffrt-dependence-t.md) items | Dependency data array. |


