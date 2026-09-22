# TransientTask_TransientTaskInfo

```c
typedef struct TransientTask_TransientTaskInfo {...} TransientTask_TransientTaskInfo
```

## Overview

A struct that describes all transient task information. The struct returns all transient task information, including the remaining quota of the current day.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Since**: 20

**Related module**: [TransientTask](capi-transienttask.md)

**Header file**: [transient_task_type.h](capi-transient-task-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t remainingQuota | Remaining quota of the current day, in ms.<br>**Since**: 20 |
| [TransientTask_DelaySuspendInfo](capi-transienttask-transienttask-delaysuspendinfo.md) transientTasks[TRANSIENT_TASK_MAX_NUM] | The info of delay suspend<br>**Since**: 20 |


