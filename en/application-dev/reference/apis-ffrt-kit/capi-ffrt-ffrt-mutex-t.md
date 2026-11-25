# ffrt_mutex_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-13T03:03:34.506Z pushedAt=2026-11-13T08:26:35.914Z nl=1 -->

```c
typedef struct {...} ffrt_mutex_t
```

## Overview

Mutex structure, used to store the internal data of a mutex.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t storage[(ffrt_mutex_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)] | Internal storage of the mutex. Do not access it directly. Manage it through APIs such as **ffrt_mutex_***. |
