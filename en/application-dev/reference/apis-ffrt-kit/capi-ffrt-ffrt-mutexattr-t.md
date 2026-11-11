# ffrt_mutexattr_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-10T03:16:46.676Z pushedAt=2026-11-10T04:56:19.933Z nl=1 -->

```c
typedef struct {...} ffrt_mutexattr_t
```

## Overview

Defines the mutex attribute struct, which is used to store the attribute information of a mutex.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| long storage | Internal storage of the mutex attribute. Do not access it directly. Initialize it through [ffrt_mutexattr_init](capi-mutex-h.md#ffrt_mutexattr_init). |


