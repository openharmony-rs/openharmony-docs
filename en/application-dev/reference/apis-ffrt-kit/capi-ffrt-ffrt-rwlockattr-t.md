# ffrt_rwlockattr_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-10T03:17:16.786Z pushedAt=2026-11-10T04:56:40.736Z nl=1 -->

```c
typedef struct {...} ffrt_rwlockattr_t
```

## Overview

Read-write lock attribute structure, used to store the attribute information of a read-write lock.

**Since**: 18

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| long storage | Internal storage of the read-write lock attributes. Do not access directly, as direct access may invalidate the read-write lock attributes. |


