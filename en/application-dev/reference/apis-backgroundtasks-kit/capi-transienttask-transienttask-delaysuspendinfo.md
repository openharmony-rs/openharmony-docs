# TransientTask_DelaySuspendInfo

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

```c
typedef struct TransientTask_DelaySuspendInfo {...} TransientTask_DelaySuspendInfo
```

## Overview

A struct that describes the returned information about a transient task. The struct returns the ID and remaining time of the transient task.

**Since**: 13

**Related module**: [TransientTask](capi-transienttask.md)

**Header file**: [transient_task_type.h](capi-transient-task-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t requestId | Request ID of a transient task.|
| int32_t actualDelayTime | Remaining time, in ms.|
