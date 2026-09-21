# updateBackgroundRunning

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## updateBackgroundRunning

```TypeScript
function updateBackgroundRunning(context: Context, bgModes: string[]): Promise<ContinuousTaskNotification>
```

Updates continuous tasks of multiple types. This API uses a promise to return the result. After a continuous task is successfully updated, there will be a notification message without prompt tone.

Before updating a continuous task, you can call [getAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-getallcontinuoustasks-f.md) to retrieve information about all existing continuous tasks. If there are no continuous tasks, the update will fail.

This API can only be used to update continuous tasks that were requested via the following APIs:

[startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback&lt;void&gt;): void](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md)

[startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise&lt;void&gt;](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-1)

[startBackgroundRunning(context: Context, bgModes: string[], wantAgent: WantAgent): Promise&lt;ContinuousTaskNotification&gt;][startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-2)

**Since:** 12

**Required permissions:** ohos.permission.KEEP_BACKGROUND_RUNNING

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. <br>For details about the application context of the FA model, see Context.<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md).<br> Note: Continuous tasks can be requested only by the UIAbility in the stage model and the ServiceAbility in the FA model. |
| bgModes | string[] | Yes | Types of continuous tasks after the update. <br>For details about the available options, see [Item](../../../task-management/continuous-task.md#use-cases).<br> Note: One or more types can be passed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ContinuousTaskNotification](arkts-backgroundtasks-backgroundtaskmanager-continuoustasknotification-i.md)&gt; | Promise that returns an object of the [ContinuousTaskNotification](arkts-backgroundtasks-backgroundtaskmanager-continuoustasknotification-i.md) type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameters types; 3. Parameter verification failed. |
| [9800001](../errorcode-backgroundTaskMgr.md#9800001-memory-operation-failure) | Memory operation failed. |
| [9800002](../errorcode-backgroundTaskMgr.md#9800002-parcel-readwrite-operation-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [9800003](../errorcode-backgroundTaskMgr.md#9800003-ipc-failure) | Internal transaction failed. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-system-service-failure) | System service operation failed. |
| [9800005](../errorcode-backgroundTaskMgr.md#9800005-long-running-task-verification-failure) | Continuous task verification failed. |
| [9800006](../errorcode-backgroundTaskMgr.md#9800006-notification-verification-failure-for-a-long-running-task) | Notification verification failed for a continuous task. |
| [9800007](../errorcode-backgroundTaskMgr.md#9800007-long-running-task-storage-failure) | Continuous task storage failed. |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    try {
      // You must call startBackgroundRunning before updateBackgroundRunning. Here it is assumed that you have called startBackgroundRunning.
      let list: Array<string> = ["audioPlayback"];
      backgroundTaskManager.updateBackgroundRunning(this.context, list).then(() => {
        console.info("Operation updateBackgroundRunning succeeded");
      }).catch((error: BusinessError) => {
        console.error(`Operation updateBackgroundRunning failed. code is ${error.code} message is ${error.message}`);
      });
    } catch (error) {
      console.error(`Operation updateBackgroundRunning failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```


<a id="updatebackgroundrunning-1"></a>

## updateBackgroundRunning

```TypeScript
function updateBackgroundRunning(context: Context, request: ContinuousTaskRequest): Promise<ContinuousTaskNotification>
```

Updates a continuous task. This API uses a promise to return the result. After a continuous task is successfully updated, there will be a notification message without prompt tone.

The following restrictions apply when updating a continuous task:

1. This API can only update continuous tasks requested via
[startBackgroundRunning(context: Context, request: ContinuousTaskRequest): Promise&lt;ContinuousTaskNotification&gt;](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-3).
2. If the main type and subtype of the background tasks are the same,
only the wants information (such as **abilityName**) in **ContinuousTaskRequest.wantAgent** can be updated. If the types are different, the update fails.
3. If the continuous task to be updated or the specified update type contains the data transmission type,
a failure message is returned.

**Since:** 21

**Required permissions:** ohos.permission.KEEP_BACKGROUND_RUNNING

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. <br>For details about the application context of the FA model, see Context.<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md).<br> Note: Continuous tasks can be requested only by the UIAbility in the stage model and the ServiceAbility in the FA model. |
| request | [ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md) | Yes | Continuous task request information, including the ID of the continuous task to be updated. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ContinuousTaskNotification](arkts-backgroundtasks-backgroundtaskmanager-continuoustasknotification-i.md)&gt; | Promise used to return the updated continuous task notification information, including the continuous task ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [9800001](../errorcode-backgroundTaskMgr.md#9800001-memory-operation-failure) | Memory operation failed. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-system-service-failure) | System service operation failed. |
| [9800005](../errorcode-backgroundTaskMgr.md#9800005-long-running-task-verification-failure) | Continuous task verification failed. |
| [9800006](../errorcode-backgroundTaskMgr.md#9800006-notification-verification-failure-for-a-long-running-task) | Notification verification failed for a continuous task. |
| [9800007](../errorcode-backgroundTaskMgr.md#9800007-long-running-task-storage-failure) | Continuous task storage failed. |
| 9800008 | The requested continuous task is not supported on this device type.<br>**Applicable version:** 26.2.0 and later |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { wantAgent, WantAgent } from '@kit.AbilityKit';
// In atomic services, please remove the WantAgent import.

export default class EntryAbility extends UIAbility {
  notificationId: number = 0; // Save the notification ID.
  continuousTaskId: number | undefined = -1; // Continuous task ID.
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      // Add the bundleName and abilityName of the application to be started. Replace them with the actual ones.
      wants: [
        {
          bundleName: "com.example.myapplication",
          abilityName: "EntryAbility"
        }
      ],
      // Set the operation type after the notification is tapped.
      actionType: wantAgent.OperationType.START_ABILITY,
      // Custom request code, which is used to identify the operation to execute.
      requestCode: 0,
      // Set the operation properties after the notification is tapped.
      wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
    };

    try {
      // Obtain the WantAgent object by using the getWantAgent API of the wantAgent module.
      // In atomic services, please replace the following line of code with wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: object) => {.
      wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: WantAgent) => {
        try {
          // You must call startBackgroundRunning before updateBackgroundRunning. Apply for a continuous task in advance.
          let modeList: Array<number> = [backgroundTaskManager.BackgroundTaskMode.MODE_LOCATION];
          let subModeList: Array<number> = [backgroundTaskManager.BackgroundTaskSubmode.SUBMODE_NORMAL_NOTIFICATION];
          let continuousTaskRequest = new backgroundTaskManager.ContinuousTaskRequest();
          continuousTaskRequest.backgroundTaskModes = modeList;
          continuousTaskRequest.backgroundTaskSubmodes = subModeList;
          continuousTaskRequest.wantAgent = wantAgentObj;
          continuousTaskRequest.combinedTaskNotification = false;
          continuousTaskRequest.continuousTaskId = this.continuousTaskId; // For the update API, the continuous task ID must be passed and the ID must exist. Otherwise, the update fails.
          backgroundTaskManager.updateBackgroundRunning(this.context, continuousTaskRequest).then((res: backgroundTaskManager.ContinuousTaskNotification) => {
            console.info("Operation updateBackgroundRunning succeeded");
            this.notificationId = res.notificationId;
          }).catch((error: BusinessError) => {
            console.error(`Operation updateBackgroundRunning failed. code is ${error.code} message is ${error.message}`);
          });
        } catch (error) {
          console.error(`Operation updateBackgroundRunning failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
      });
    } catch (error) {
      console.error(`Operation getWantAgent failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```
