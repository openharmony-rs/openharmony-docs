# setBackgroundTaskState (System API)

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## setBackgroundTaskState

```TypeScript
function setBackgroundTaskState(stateInfo: BackgroundTaskStateInfo): void
```

Sets the authorization information of a continuous task.

**Since:** 22

**Required permissions:** ohos.permission.SET_BACKGROUND_TASK_STATE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| stateInfo | [BackgroundTaskStateInfo](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskstateinfo-i-sys.md) | Yes | Required authorization information, including the user ID, application bundle name, and application clone ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-system-service-failure) | System service operation failed. |
| [9800005](../errorcode-backgroundTaskMgr.md#9800005-continuous-task-verification-failure) | Continuous task verification failed. |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    // Update the parameters based on the actual situation.
    let backgroundTaskStateInfo: backgroundTaskManager.BackgroundTaskStateInfo = {
        userId: 100,
        bundleName: 'com.example.continuoustask',
        appIndex: 0,
        authResult: backgroundTaskManager.UserAuthResult.DENIED
    };
    backgroundTaskManager.setBackgroundTaskState(backgroundTaskStateInfo);
    console.info('Operation setBackgroundTaskState succeeded.');
} catch (error) {
    console.error(`Operation setBackgroundTaskState failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}
```
