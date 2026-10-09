# ffrt_queue_attr_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T01:58:07.892Z pushedAt=2026-07-20T02:25:43.470Z -->

```c
typedef struct {...} ffrt_queue_attr_t
```

## Overview

Queue attribute struct, used to store the attribute information of a queue.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t storage[(ffrt_queue_attr_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)] | Internal storage of the queue attributes. Do not access it directly. Manage the content via [ffrt_queue_attr_init](capi-queue-h.md#ffrt_queue_attr_init) and APIs such as `ffrt_queue_attr_set_*`. |