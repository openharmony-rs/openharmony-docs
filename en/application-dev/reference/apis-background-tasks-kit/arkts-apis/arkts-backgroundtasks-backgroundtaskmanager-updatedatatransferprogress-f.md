# updateDataTransferProgress

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## updateDataTransferProgress

```TypeScript
function updateDataTransferProgress(context: Context, progressInfo: DataTransferProgress): void
```

Update notification. Only data transfer ContinuousTasks are supported.

**Since:** 26.0.1

**Required permissions:** ohos.permission.KEEP_BACKGROUND_RUNNING

**Model restriction:** This API can be used only in the stage model.

<!--Device-backgroundTaskManager-function updateDataTransferProgress(context: Context, progressInfo: DataTransferProgress): void--><!--Device-backgroundTaskManager-function updateDataTransferProgress(context: Context, progressInfo: DataTransferProgress): void-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. |
| progressInfo | [DataTransferProgress](arkts-backgroundtasks-backgroundtaskmanager-datatransferprogress-i.md) | Yes | Notify progress data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-system-service-failure) | System service operation failed. |
| [9800005](../errorcode-backgroundTaskMgr.md#9800005-long-running-task-verification-failure) | Continuous task verification failed. |
| [9800006](../errorcode-backgroundTaskMgr.md#9800006-notification-verification-failure-for-a-long-running-task) | Notification verification failed for a continuous task. |
| [9800007](../errorcode-backgroundTaskMgr.md#9800007-long-running-task-storage-failure) | Continuous task storage failed. |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';
import { wantAgent, WantAgent } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  continuousTaskId: number = -1; // ID of the continuous task
  onCreate() {
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      // List of operations to be executed after the notification is clicked.
      wants: [
        {
          bundleName: 'com.example.myapplication',
          abilityName: 'EntryAbility'
        }
      ],
      // Type of the operation to perform after the notification is clicked.
      actionType: wantAgent.OperationType.START_ABILITY,
      // Custom request code.
      requestCode: 0,
      // Execution attribute of the operation to perform after the notification is clicked.
      wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
    };
    let progress: backgroundTaskManager.ProgressInfo = {
      title: 'Notification title', // Mandatory
      fileName: 'Notification content', // Mandatory
      progressValue: 20, // The app updates the progress, which is user-defined.
      isMute: false, // Whether to mute the notification when the progress reaches 100%. This parameter is user-defined.
    };

    try {
      // Obtain the WantAgent object by using the getWantAgent API of the wantAgent module.
      wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: WantAgent) => {
        try {
          // Request a continuous data transfer task.
          let list: Array<string> = ['dataTransfer'];
          backgroundTaskManager.startBackgroundRunning(this.context, list, wantAgentObj).then((res: backgroundTaskManager.ContinuousTaskNotification) => {
            console.info('Operation startBackgroundRunning succeeded');
            // For a continuous task of the data transfer type, the app can use the continuous task ID returned in res to update the notification, for example, sending a template notification with a progress bar.
            this.continuousTaskId = res.continuousTaskId;
            try {
              let progressInfo: backgroundTaskManager.DataTransferProgress = {
                continuousTaskId: this.continuousTaskId,
                wantAgent: wantAgentObj,
                progressInfo: progress,
              }
              // Update notification
              backgroundTaskManager.updateDataTransferProgress(this.context, progressInfo);
              console.info('Operation updateDataTransferProgress succeeded');
            } catch(error) {
              console.error(`Operation updateDataTransferProgress failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
            }
          }).catch((error: BusinessError) => {
            console.error(`Operation startBackgroundRunning failed. code is ${error.code} message is ${error.message}`);
          });
        } catch (error) {
          console.error(`Operation startBackgroundRunning failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
      });
    } catch (error) {
      console.error(`Operation getWantAgent failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```
