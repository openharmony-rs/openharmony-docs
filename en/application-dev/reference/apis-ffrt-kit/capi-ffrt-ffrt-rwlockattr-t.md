# ffrt_rwlockattr_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T01:58:30.955Z pushedAt=2026-07-20T02:25:55.354Z -->

```c
typedef struct {...} ffrt_rwlockattr_t
```

## Overview

Read-write lock attribute struct, used to store the attribute information of a read-write lock.

**Since**: 18

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| long storage | Internal storage of the read-write lock attributes. Do not access it directly, as direct access may cause the read-write lock attributes to become invalid. |