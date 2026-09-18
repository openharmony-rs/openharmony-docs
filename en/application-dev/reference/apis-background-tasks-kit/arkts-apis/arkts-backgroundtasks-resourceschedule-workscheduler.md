# @ohos.resourceschedule.workScheduler(Deferred Task Scheduling)

The **workScheduler** module provides the APIs for registering, canceling, and querying deferred tasks. You can use the APIs to register tasks that do not have high requirements on real-time performance as deferred tasks. The system schedules and executes the deferred tasks at an appropriate time, subject to the storage space, power consumption, and more. For details, see [Deferred Task Scheduling](../../../task-management/work-scheduler.md).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

## Modules to Import

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getWorkStatus](arkts-backgroundtasks-workscheduler-getworkstatus-f.md) | Obtains the information a deferred task. This API uses an asynchronous callback to return the result. |
| [getWorkStatus](arkts-backgroundtasks-workscheduler-getworkstatus-f.md) | Obtains the information a deferred task. This API uses a promise to return the result. |
| [isLastWorkTimeOut](arkts-backgroundtasks-workscheduler-islastworktimeout-f.md) | Checks whether the last execution of a task timed out. This API uses an asynchronous callback to return the result. |
| [isLastWorkTimeOut](arkts-backgroundtasks-workscheduler-islastworktimeout-f.md) | Checks whether the last execution of a task timed out. This API uses an asynchronous callback to return the result. |
| [isLastWorkTimeOut](arkts-backgroundtasks-workscheduler-islastworktimeout-f.md) | Checks whether the last execution of a task timed out. This API uses a promise to return the result. |
| [obtainAllWorks](arkts-backgroundtasks-workscheduler-obtainallworks-f.md) | Obtains all the deferred tasks. This API uses an asynchronous callback to return the result. |
| [obtainAllWorks](arkts-backgroundtasks-workscheduler-obtainallworks-f.md) | Obtains all the deferred tasks. This API uses an asynchronous callback to return the result. |
| [obtainAllWorks](arkts-backgroundtasks-workscheduler-obtainallworks-f.md) | Obtains all the deferred tasks. This API uses a promise to return the result. |
| [startWork](arkts-backgroundtasks-workscheduler-startwork-f.md) | Requests a deferred task. Upon successful request, the deferred task is added to the execution queue and will be executed by the system once the trigger conditions are met. |
| [stopAndClearWorks](arkts-backgroundtasks-workscheduler-stopandclearworks-f.md) | Stops and clears all the deferred tasks. |
| [stopWork](arkts-backgroundtasks-workscheduler-stopwork-f.md) | Stops a deferred task. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [resetExecFrequency](arkts-backgroundtasks-workscheduler-resetexecfrequency-f-sys.md) | Reset the execution frequency. |
| [setExecFrequency](arkts-backgroundtasks-workscheduler-setexecfrequency-f-sys.md) | Set the execution frequency. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [WorkInfo](arkts-backgroundtasks-workscheduler-workinfo-i.md) | Represents the deferred task information, which is used to set the trigger condition. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [FrequencyInfo](arkts-backgroundtasks-workscheduler-frequencyinfo-i-sys.md) | Execution frequency information. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [BatteryStatus](arkts-backgroundtasks-workscheduler-batterystatus-e.md) | Enumerates the battery status that triggers the deferred task callback. |
| [ChargingType](arkts-backgroundtasks-workscheduler-chargingtype-e.md) | Enumerates the charging types that trigger deferred task callback. |
| [NetworkType](arkts-backgroundtasks-workscheduler-networktype-e.md) | Enumerates the network types that trigger deferred task callback. |
| [StorageRequest](arkts-backgroundtasks-workscheduler-storagerequest-e.md) | Enumerates the storage status that triggers the deferred task callback. |

<!--Del-->
### Constants(System API)

| Name | Description |
| --- | --- |
| [EXECUTE_IMMEDIATE](arkts-backgroundtasks-workscheduler-con-sys.md#execute_immediate) | Whether the requested task is executed immediately. |
| [WORK_SCHEDULER_CONDITION](arkts-backgroundtasks-workscheduler-con-sys.md#work_scheduler_condition) | The last condition met when the current task is triggered. |
<!--DelEnd-->
