# ffrt_rwlock_t

```c
typedef struct ffrt_rwlock_t {...} ffrt_rwlock_t
```

## Overview

Defines the rwlock structure used to store internal data of the rwlock.

**Since**: 18

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [uint32_t storage[(ffrt_rwlock_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)]](#sizeof) | Internal storage backing the rwlock. Do not access directly; use the `ffrt_rwlock_*` APIs. |

## Member function description

### sizeof()

```c
uint32_t storage[(ffrt_rwlock_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)]
```

**Description**

Internal storage backing the rwlock. Do not access directly; use the `ffrt_rwlock_*` APIs.


