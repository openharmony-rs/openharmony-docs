# TransientTask_DelaySuspendInfo

```c
struct TransientTask_DelaySuspendInfo {...}
```

## Overview

A struct that describes the returned information about a transient task. The struct returns the ID and remaining time of the transient task.

<!--Device-struct TransientTask_DelaySuspendInfo {...}--><!--Device-struct TransientTask_DelaySuspendInfo {...}-End-->

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Since**: 13

**Related module**: [TransientTask](capi-background-tasks-kit-transienttask.md)

**Header file**: [transient_task_type.h](capi-transient-task-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t requestId | Request ID of a transient task.<br>**Since**: 13 |
| int32_t actualDelayTime | Remaining time, in ms.<br>**Since**: 13 |


