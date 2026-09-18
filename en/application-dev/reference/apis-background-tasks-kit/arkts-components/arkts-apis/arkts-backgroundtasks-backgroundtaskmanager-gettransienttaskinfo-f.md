# getTransientTaskInfo

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## getTransientTaskInfo

```TypeScript
function getTransientTaskInfo(): Promise<TransientTaskInfo>
```

Obtains all transient task information, including the remaining quota of the current day. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[TransientTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-transienttaskinfo-i.md)&gt; | Promise that returns all transient task information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9900001](../errorcode-backgroundTaskMgr.md#9900001-caller-information-verification-failure-for-a-transient-task) | Caller information verification failed for a transient task. |
| [9900003](../errorcode-backgroundTaskMgr.md#9900003-parcel-operation-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [9900004](../errorcode-backgroundTaskMgr.md#9900004-system-service-failure) | System service operation failed. |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  backgroundTaskManager.getTransientTaskInfo().then((res: backgroundTaskManager.TransientTaskInfo) => {
    console.info(`Operation getTransientTaskInfo succeeded. data: ` + JSON.stringify(res));
  }).catch((error : BusinessError) => {
    console.error(`Operation getTransientTaskInfo failed. code is ${error.code} message is ${error.message}`);
  });
} catch (error) {
  console.error(`Operation getTransientTaskInfo failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}
```
