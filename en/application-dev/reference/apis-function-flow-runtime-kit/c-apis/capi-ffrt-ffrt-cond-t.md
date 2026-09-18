# ffrt_cond_t

```c
typedef struct ffrt_cond_t {...} ffrt_cond_t
```

## Overview

Defines the condition variable structure used to store internal data of the condition variable.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [uint32_t storage[(ffrt_cond_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)]](#sizeof) | Internal storage backing the condition variable. Do not access directly; use the `ffrt_cond_*` APIs. |

## Member function description

### sizeof()

```c
uint32_t storage[(ffrt_cond_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)]
```

**Description**

Internal storage backing the condition variable. Do not access directly; use the `ffrt_cond_*` APIs.


