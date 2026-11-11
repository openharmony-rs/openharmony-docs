# ffrt_rwlock_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-10T03:17:13.180Z pushedAt=2026-11-10T04:56:36.327Z nl=1 -->

```c
typedef struct {...} ffrt_rwlock_t
```

## Overview

Read-write lock struct used to store the internal data of a read-write lock.

**Since**: 18

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t storage[(ffrt_rwlock_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)] | Internal storage of the read-write lock. Do not access it directly. Manage it through APIs such as `ffrt_rwlock_*`. |
