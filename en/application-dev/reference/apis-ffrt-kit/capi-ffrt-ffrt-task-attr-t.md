# ffrt_task_attr_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-13T03:04:40.950Z pushedAt=2026-11-13T08:28:24.678Z nl=1 -->

```c
typedef struct {...} ffrt_task_attr_t
```

## Overview

Task attribute structure, used to store the attribute information of a task.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t storage[(ffrt_task_attr_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)] | Internal storage of the task attributes. Do not access it directly. Manage its content using APIs such as [ffrt_task_attr_init](capi-task-h.md#ffrt_task_attr_init) and **ffrt_task_attr_set_***. |
