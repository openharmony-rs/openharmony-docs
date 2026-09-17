# TransientTask_TransientTaskInfo

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=9920121677da308fdab3c8882d0cb971a267b244 translatedAt=2026-09-15T12:46:46.826Z pushedAt=2026-09-17T02:20:58.617Z -->

```c
typedef struct TransientTask_TransientTaskInfo {...} TransientTask_TransientTaskInfo
```

## Overview

A struct that describes all transient task information. It is used to return the total remaining quota of the current day and information about all applied transient tasks.

**Since**: 20

**Related module**: [TransientTask](capi-transienttask.md)

**Header file**: [transient_task_type.h](capi-transient-task-type-h.md)

## Summary

### Member Variables

| Name                                                                                                                           | Description|
|-------------------------------------------------------------------------------------------------------------------------------| -- |
| int32_t remainingQuota                                                                                                        | Total remaining time quota of transient tasks on the current day, in milliseconds. The value range is [0, 600000]. |
| [TransientTask_DelaySuspendInfo](capi-transienttask-transienttask-delaysuspendinfo.md) transientTasks[[TRANSIENT_TASK_MAX_NUM](capi-transient-task-type-h.md#macro-definition)] | All requested transient tasks (a maximum of three tasks can be requested at a time), including the task request ID and remaining time, in milliseconds. |
