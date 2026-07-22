# ffrt_mutexattr_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T01:57:57.595Z pushedAt=2026-07-20T02:25:38.015Z -->

```c
typedef struct {...} ffrt_mutexattr_t
```

## Overview

Mutex attribute struct, used to store the attribute information of a mutex.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| long storage | Internal storage of the mutex attributes. Do not access it directly. Initialize it using [ffrt_mutexattr_init](capi-mutex-h.md#ffrt_mutexattr_init). |