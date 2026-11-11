# ffrt_queue_attr_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-10T03:16:50.289Z pushedAt=2026-11-10T04:56:24.406Z nl=1 -->

```c
typedef struct {...} ffrt_queue_attr_t
```

## Overview

Queue attribute struct that stores the attribute information of a queue.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t storage[(ffrt_queue_attr_storage_size + sizeof(uint32_t) - 1) / sizeof(uint32_t)] | Internal storage of the queue attribute. Do not access it directly. Manage the content through APIs such as [ffrt_queue_attr_init](capi-queue-h.md#ffrt_queue_attr_init) and `ffrt_queue_attr_set_*`. |
