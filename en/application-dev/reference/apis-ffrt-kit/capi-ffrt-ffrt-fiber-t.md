# ffrt_fiber_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-13T03:02:17.955Z pushedAt=2026-11-13T08:20:37.224Z nl=1 -->

```c
typedef struct {...} ffrt_fiber_t
```

## Overview

Fiber structure, used to store the fiber execution context.

**Since**: 20

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uintptr_t storage[ffrt_fiber_storage_size] | Internal storage of the fiber execution context. Do not access it directly. Initialize it using [ffrt_fiber_init](capi-fiber-h.md#ffrt_fiber_init), and switch it using [ffrt_fiber_switch](capi-fiber-h.md#ffrt_fiber_switch). |


