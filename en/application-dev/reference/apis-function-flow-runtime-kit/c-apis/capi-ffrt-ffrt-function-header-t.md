# ffrt_function_header_t

```c
typedef struct ffrt_function_header_t {...} ffrt_function_header_t
```

## Overview

Defines a task executor, used to define the task execution and destruction callbacks.<br> The exec callback is invoked when the task is scheduled, and the destroy callback is invoked after the task completes to release task-related resources. Together they manage the full lifecycle of an FFRT task.

<!--Device-typedef struct ffrt_function_header_t {...} ffrt_function_header_t--><!--Device-typedef struct ffrt_function_header_t {...} ffrt_function_header_t-End-->

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-function-flow-runtime-kit-ffrt.md)

**Header file**: [type_def.h](capi-type-def-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) exec | Function used to execute a task. Called by the framework when the task is scheduled.<br><!--Device-ffrt_function_t exec--><!--Device-ffrt_function_t exec-End--> |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) destroy | Function used to destroy a task. Called by the framework after task execution to release resources.<br><!--Device-ffrt_function_t destroy--><!--Device-ffrt_function_t destroy-End--> |
| uint64_t reserve[2] | Reserved field. Need to be set to 0.<br><!--Device-uint64_t reserve[2]--><!--Device-uint64_t reserve[2]-End--> |


