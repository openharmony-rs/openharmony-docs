# ffrt_deps_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-10T03:15:49.566Z pushedAt=2026-11-10T04:55:54.173Z nl=1 -->

```c
typedef struct {...} ffrt_deps_t
```

## Overview

Dependency struct that stores the dependency list of a task.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t len | Number of dependencies. |
| const [ffrt_dependence_t*](capi-ffrt-ffrt-dependence-t.md) items | Array of dependency data. |


