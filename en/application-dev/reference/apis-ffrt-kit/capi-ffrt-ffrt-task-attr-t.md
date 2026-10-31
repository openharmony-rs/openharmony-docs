# ffrt_task_attr_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T01:58:31.280Z pushedAt=2026-07-20T02:18:01.667Z -->

```c
typedef struct {...} ffrt_task_attr_t
```

## Overview

Task attribute struct, used to store the attribute information of a task.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t storage[(ffrt_task_attr_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)] | Internal storage of the task attributes. Do not access directly. Manage the content through [ffrt_task_attr_init](capi-task-h.md#ffrt_task_attr_init) and APIs such as `ffrt_task_attr_set_*`. |