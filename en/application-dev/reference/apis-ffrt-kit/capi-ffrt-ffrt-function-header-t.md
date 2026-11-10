# ffrt_function_header_t

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-10T03:16:21.366Z pushedAt=2026-11-10T04:56:03.673Z nl=1 -->

```c
typedef struct {...} ffrt_function_header_t
```

## Overview

Task execution body, used to define the execution and destruction callbacks of a task. The `exec` callback is invoked when the task is scheduled, and the `destroy` callback is invoked after the task is complete to release task-related resources. Together, they manage the complete lifecycle of an FFRT task.

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) exec | Function for executing the task. Called by the framework when the task is scheduled. |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) destroy | Function for destroying the task. Called by the framework to release resources after the task is executed. |
| uint64_t reserve[2] | Reserved field. Set it to 0. |


