# @ohos.resourceschedule.workScheduler (Deferred Task Scheduling) (System API)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

This module provides the APIs for registering, canceling, and querying deferred tasks. You can use the APIs to register tasks that do not have high requirements on real-time performance as deferred tasks. The system schedules and executes the deferred tasks at an appropriate time, subject to the storage space, power consumption, temperature, and more.

**Since:** 26.0.0

## Modules to Import

```ts
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## Constants

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**System API:** This is a system API.

| Name| Type| Value| Description|
| -------- | -------- | -------- | -------- |
| WORK_SCHEDULER_CONDITION | string | 'WORK_SCHEDULER_CONDITION' | Last condition that must be met to trigger the current task. This parameter can be used in [onWorkStart](js-apis-WorkSchedulerExtensionAbility.md#onworkstart) as a key of **workInfo.parameters**.|
| EXECUTE_IMMEDIATE | string | 'executeImmediate' | Whether the requested task is executed immediately. This parameter can be used in [startWork](js-apis-resourceschedule-workScheduler.md#workschedulerstartwork) as a key of **workInfo.parameters**.|
