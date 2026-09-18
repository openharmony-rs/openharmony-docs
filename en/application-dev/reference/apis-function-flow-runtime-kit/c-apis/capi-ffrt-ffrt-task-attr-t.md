# ffrt_task_attr_t

```c
typedef struct ffrt_task_attr_t {...} ffrt_task_attr_t
```

## Overview

Defines the task attribute structure used to store task attribute information.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [uint32_t storage[(ffrt_task_attr_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)]](#sizeof) | Internal storage backing the task attribute. Do not access directly; use the {@link ffrt_task_attr_init} and `ffrt_task_attr_set_*` APIs to manage contents. |

## Member function description

### sizeof()

```c
uint32_t storage[(ffrt_task_attr_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)]
```

**Description**

Internal storage backing the task attribute. Do not access directly; use the {@link ffrt_task_attr_init} and `ffrt_task_attr_set_*` APIs to manage contents.


