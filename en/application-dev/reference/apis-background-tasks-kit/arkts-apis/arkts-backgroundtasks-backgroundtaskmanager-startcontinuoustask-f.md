# startContinuousTask

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## startContinuousTask

```TypeScript
function startContinuousTask(context: Context, request: ContinuousTaskRequest): Promise<number>
```

Requests a continuous task. This API allows a UIAbility (ServiceAbility in the FA model) to request multiple continuous tasks and uses a promise to return the result. When using this API to request a continuous task, its notification can be combined with that of an existing continuous task. For details, see [ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md).

A maximum of 10 continuous tasks can be created simultaneously. Upon successful creation of a continuous task, a notification will be sent without a prompt tone.

If a continuous task requested via this API includes multiple task types (including data transmission tasks), two notifications will appear in the notification panel: one for the data transmission task and the other for the remaining tasks. Removing either notification will cancel the continuous task and remove the other notification. The continuous task notification ID returned by the API is the ID of the data transmission type, which is used to update the data transmission progress.

**Since:** 26.0.1

**Required permissions:** ohos.permission.KEEP_BACKGROUND_RUNNING

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-backgroundTaskManager-function startContinuousTask(context: Context, request: ContinuousTaskRequest): Promise<int>--><!--Device-backgroundTaskManager-function startContinuousTask(context: Context, request: ContinuousTaskRequest): Promise<int>-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. <br>For details about the application context of the FA model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context.md).<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md).<br> Note: Continuous tasks can be requested only by the UIAbility in the stage model and the ServiceAbility in the FA model. |
| request | [ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md) | Yes | Request information of a continuous task, including the main type and subtype. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the continuous task ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9800001](../errorcode-backgroundTaskMgr.md#9800001-memory-operation-failure) | Memory operation failed. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-system-service-failure) | System service operation failed. |
| [9800005](../errorcode-backgroundTaskMgr.md#9800005-long-running-task-verification-failure) | Continuous task verification failed. |
| [9800006](../errorcode-backgroundTaskMgr.md#9800006-notification-verification-failure-for-a-long-running-task) | Notification verification failed for a continuous task. |
| [9800007](../errorcode-backgroundTaskMgr.md#9800007-long-running-task-storage-failure) | Continuous task storage failed. |
| 9800008 | The requested continuous task is not supported on this device type. |
