# ffrt_dependence_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T01:57:07.794Z pushedAt=2026-07-20T02:25:04.506Z -->

```c
typedef struct {...} ffrt_dependence_t
```

## Overview

Dependency data item struct, used to describe a single dependency relationship between tasks.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [ffrt_dependence_type_t](capi-type-def-h.md#ffrt_dependence_type_t) type | Dependency type. |
| const void* ptr | Dependency pointer. It points to data for data dependency, and points to a task handle for task dependency. |