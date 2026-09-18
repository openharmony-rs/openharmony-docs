# ffrt_dependence_t

```c
typedef struct ffrt_dependence_t {...} ffrt_dependence_t
```

## Overview

Defines the dependency data structure used to describe a single dependency between tasks.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [ffrt_dependence_type_t](capi-type-def-h.md#ffrt_dependence_type_t) type | Dependency type. |
| const void* ptr | Dependency pointer. Points to the data (data dependency) or task handle (task dependency). |


