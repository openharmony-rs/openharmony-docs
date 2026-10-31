# ffrt_function_header_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T01:57:40.666Z pushedAt=2026-07-20T02:25:23.762Z -->

```c
typedef struct {...} ffrt_function_header_t
```

## Overview

Task execution struct, used to define the execution and destruction callbacks of a task. The `exec` callback is invoked when the task is scheduled, and the `destroy` callback is invoked after the task completes to release task-related resources. Together, the two callbacks manage the complete lifecycle of an FFRT task.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) exec | Function for executing a task. It is called by the framework when the task is scheduled. |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) destroy | Function for destroying a task. It is called by the framework to release resources after the task execution is complete. |
| uint64_t reserve[2] | Reserved field. It must be set to **0**. |