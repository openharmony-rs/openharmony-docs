# requestSuspendDelay

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## requestSuspendDelay

```TypeScript
function requestSuspendDelay(reason: string, callback: Callback<void>): DelaySuspendInfo
```

Requests a transient task.

> **NOTE:** 
> 
> For details about the constraints on requesting and using a transient task, see
> [Transient Task (ArkTS)](../../../task-management/transient-task.md#constraints).

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reason | string | Yes | Reason for requesting the transient task. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback used to notify the application that the transient task is about to time out. Generally, the callback is invoked 6 seconds before the timeout. |

**Return value:**

| Type | Description |
| --- | --- |
| [DelaySuspendInfo](arkts-backgroundtasks-backgroundtaskmanager-delaysuspendinfo-i.md) | Information about the transient task. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameters types. |
| [9800001](../errorcode-backgroundTaskMgr.md#9800001-memory-operation-failure) | Memory operation failed. |
| [9800002](../errorcode-backgroundTaskMgr.md#9800002-parcel-operation-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [9800003](../errorcode-backgroundTaskMgr.md#9800003-ipc-failure) | Internal transaction failed. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-system-service-failure) | System service operation failed. |
| [9900001](../errorcode-backgroundTaskMgr.md#9900001-caller-information-verification-failure-for-a-transient-task) | Caller information verification failed for a transient task. |
| [9900002](../errorcode-backgroundTaskMgr.md#9900002-transient-task-verification-failure) | Transient task verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';

let myReason = 'test requestSuspendDelay';
try {
  let delayInfo = backgroundTaskManager.requestSuspendDelay(myReason, () => {
  // Callback function, which is triggered when the transient task is about to time out. The application can carry out data clear and annotation, and cancel the task in the callback.
  // The callback is independent of the service of the application. After the request for the transient task is successful, the application normally executes its own service logic.
    console.info("Request suspension delay will time out.");
  })
  let id = delayInfo.requestId;
  let time = delayInfo.actualDelayTime;
  console.info("The requestId is: " + id);
  console.info("The actualDelayTime is: " + time);
} catch (error) {
  console.error(`requestSuspendDelay failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}
```
