# ffrt_rwlockattr_t

```c
typedef struct ffrt_rwlockattr_t {...} ffrt_rwlockattr_t
```

## Overview

Defines the rwlock attribute structure used to store rwlock attribute information.

**Since**: 18

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| long storage | Internal storage backing the rwlock attribute. Do not access directly; direct access may cause the rwlock attribute to become invalid. |


