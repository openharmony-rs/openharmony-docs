# TransientTask_DelaySuspendInfo

```c
typedef struct TransientTask_DelaySuspendInfo {...} TransientTask_DelaySuspendInfo
```

## Overview

A struct that describes the returned information about a transient task. The struct returns the ID and remaining time of the transient task.

**Since**: 13

**Related module**: [TransientTask](capi-transienttask.md)

**Header file**: [transient_task_type.h](capi-transient-task-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t requestId | Request ID of a transient task.<br>**Since**: 13 |
| int32_t actualDelayTime | Remaining time, in ms.<br>**Since**: 13 |


