# TransientTask_DelaySuspendInfo

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=531e9eb172de84358a19bcfc47d3cdd7f3217a90 translatedAt=2026-09-15T12:44:00.879Z pushedAt=2026-09-17T02:11:44.290Z -->

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
| int32_t actualDelayTime | Remaining time, in milliseconds. The value range is [0, 180000]. |
