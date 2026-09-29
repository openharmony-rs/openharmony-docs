# unregisterTask

## Modules to Import

```TypeScript
import { backgroundLoader } from '@kit.BackgroundTasksKit';
```

## unregisterTask

```TypeScript
function unregisterTask(taskInfo: TaskInfo): void
```

Unregister background load task.

**Since:** 26.2.0

**Required permissions:** ohos.permission.KEEP_BACKGROUND_RUNNING

**Model restriction:** This API can be used only in the stage model.

<!--Device-backgroundLoader-function unregisterTask(taskInfo: TaskInfo): void--><!--Device-backgroundLoader-function unregisterTask(taskInfo: TaskInfo): void-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskInfo | [TaskInfo](arkts-backgroundtasks-backgroundloader-taskinfo-i.md) | Yes |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [9700003](../errorcode-workScheduler.md#9700003-system-service-failure) | System service operation failed. |
| [9700004](../errorcode-workScheduler.md#9700004-parameter-verification-failed) | Check on taskInfo failed. |
