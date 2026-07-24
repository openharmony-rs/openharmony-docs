# ffrt_fiber_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T01:57:32.964Z pushedAt=2026-07-20T02:25:18.283Z -->

```c
typedef struct {...} ffrt_fiber_t
```

## Overview

Fiber struct, used to store the fiber execution context.

**Since**: 20

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uintptr_t storage[ffrt_fiber_storage_size] | Internal storage of the fiber execution context. Do not access directly. Initialize it via [ffrt_fiber_init](capi-fiber-h.md#ffrt_fiber_init), and perform switching via [ffrt_fiber_switch](capi-fiber-h.md#ffrt_fiber_switch). |