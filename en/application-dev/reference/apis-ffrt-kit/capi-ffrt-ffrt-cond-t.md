# ffrt_cond_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-13T03:01:24.872Z pushedAt=2026-11-13T08:19:24.961Z nl=1 -->

```c
typedef struct {...} ffrt_cond_t
```

## Overview

Condition variable structure, used to store the internal data of a condition variable.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t storage[(ffrt_cond_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)] | Internal storage of the condition variable. Do not access it directly. Manage it using API such as **ffrt_cond_***. |
