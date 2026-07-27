# ffrt_deps_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T01:57:03.707Z pushedAt=2026-07-20T02:25:13.352Z -->

```c
typedef struct {...} ffrt_deps_t
```

## Overview

Dependency struct, used to save the dependency list of a task.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t len | Number of dependencies. |
| const [ffrt_dependence_t*](capi-ffrt-ffrt-dependence-t.md) items | Pointer to the dependency data array. |