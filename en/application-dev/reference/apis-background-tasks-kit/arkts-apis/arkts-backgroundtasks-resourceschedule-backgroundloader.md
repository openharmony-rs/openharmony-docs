# @ohos.resourceschedule.backgroundLoader

The **BackgroundLoader** module provides the APIs for registering, unregistering and querying tasks. You can use these APIs to register tasks that need to be loaded in the background. The system schedules and executes these deferred tasks at an appropriate time, subject to the storage space, power consumption.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

## Modules to Import

```TypeScript
import { backgroundLoader } from '@kit.BackgroundTasksKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [finishTask](arkts-backgroundtasks-backgroundloader-finishtask-f.md) | Finish background load task. |
| [getTaskInfo](arkts-backgroundtasks-backgroundloader-gettaskinfo-f.md) | Obtains the information of a background load task. This API returns the result via a promise. |
| [registerTask](arkts-backgroundtasks-backgroundloader-registertask-f.md) | Register background load task. |
| [unregisterTask](arkts-backgroundtasks-backgroundloader-unregistertask-f.md) | Unregister background load task. |

### Interfaces

| Name | Description |
| --- | --- |
| [TaskInfo](arkts-backgroundtasks-backgroundloader-taskinfo-i.md) | Represents the background load task information, which is used to register task. |
| [TaskStopInfo](arkts-backgroundtasks-backgroundloader-taskstopinfo-i.md) | Represents the background load task stop information, which is used to ON_STOP function. |

### Enums

| Name | Description |
| --- | --- |
| [StopCode](arkts-backgroundtasks-backgroundloader-stopcode-e.md) | Enumerates the stop code, which is used to ON_STOP function. |

### Constants

| Name | Description |
| --- | --- |
| [ON_START](arkts-backgroundtasks-backgroundloader-con.md#on_start) | Start task method. |
| [ON_STOP](arkts-backgroundtasks-backgroundloader-con.md#on_stop) | Stop task method. |
