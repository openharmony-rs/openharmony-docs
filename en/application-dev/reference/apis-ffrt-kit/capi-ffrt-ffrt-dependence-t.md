# ffrt_dependence_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-13T03:01:23.684Z pushedAt=2026-11-13T08:20:04.981Z nl=1 -->

```c
typedef struct {...} ffrt_dependence_t
```

## Overview

Dependency data item structure, used to describe a single dependency relationship between tasks.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [ffrt_dependence_type_t](capi-type-def-h.md#ffrt_dependence_type_t) type | Dependency type. |
| const void* ptr | Dependency pointer. It points to the data for a data dependency, and points to the task handle for a task dependency. |


