# ContinuousTaskRequest

Specifies details of the continuous task being requested or updated. It is typically used as input for the [startBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md) and [updateBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md) APIs. Note that:

1. When requesting a continuous task via
[startBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md), notifications will be combined if the main type and subtype of the continuous task to be requested are the same as those of the existing continuous task in the current application, and the **combinedTaskNotification** value is **true** for both tasks. Otherwise, notifications will not be combined.
2. Notifications will not be combined if the continuous task has no notification.
For details about whether notifications are sent for the continuous task, see [BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md).
3. Notifications cannot be combined if the continuous task includes data transmission.
4. Notifications that have been combined cannot be canceled.
If notifications have been combined, they cannot be updated to uncombined.
5. After notifications are combined, tapping the notification will redirect to the UIAbility
corresponding to the first requested continuous task. If the update API is called, the redirection will target the UIAbility corresponding to the last updated continuous task.
6. When the [updateBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md)
API is called to update a continuous task, the input **continuousTaskId** must exist. Otherwise, the update fails.
7. Continuous tasks of the [MODE_SPECIAL_SCENARIO_PROCESSING](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md) type
are supported since API version 22. This task type must be used independently and notifications cannot be combined. Specifically, when you request or update a continuous task, it must be of the **MODE_SPECIAL_SCENARIO_PROCESSING** type. Otherwise, an error is returned.

**Since:** 21

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## checkSpecialScenarioAuth

```TypeScript
checkSpecialScenarioAuth(context: Context): Promise<UserAuthResult>
```

Checks whether the user has authorized tasks to run continuously in the background. This API uses a promise to return the result. An exception will be thrown if unauthorized.

**Since:** 22

**Required permissions:** ohos.permission.KEEP_BACKGROUND_RUNNING

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. <br>For details about the application context of the FA model, see Context.<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md).<br> Note: Continuous tasks can be requested only by the UIAbility in the stage model and the ServiceAbility in the FA model. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[UserAuthResult](arkts-backgroundtasks-backgroundtaskmanager-userauthresult-e.md)&gt; | Promise used to return the user authorization result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-system-service-failure) | System service operation failed. |
| [9800005](../errorcode-backgroundTaskMgr.md#9800005-continuous-task-verification-failure) | Continuous task verification failed. |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    try {
      let continuousTaskRequest = new backgroundTaskManager.ContinuousTaskRequest();
      continuousTaskRequest.checkSpecialScenarioAuth(this.context).then((res: backgroundTaskManager.UserAuthResult) => {
        console.info('Operation checkSpecialScenarioAuth succeeded. data: ' + JSON.stringify(res));
      }).catch((error: BusinessError) => {
        console.error(`Operation checkSpecialScenarioAuth failed. code is ${error.code} message is ${error.message}`);
      });
    } catch (error) {
      console.error(`Operation checkSpecialScenarioAuth failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```

## checkSpecialScenarioAuthResult

```TypeScript
checkSpecialScenarioAuthResult(context: Context): Promise<UserAuthResult>
```

Check whether the application can request MODE_SPECIAL_SCENARIO_PROCESSING. No exception will be thrown whether authorized or not.

**Since:** 26.0.0

**Required permissions:** ohos.permission.KEEP_BACKGROUND_RUNNING

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | App running context. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[UserAuthResult](arkts-backgroundtasks-backgroundtaskmanager-userauthresult-e.md)&gt; | The promise returns the result of user authorization. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-system-service-failure) | System service operation failed. |
| [9800005](../errorcode-backgroundTaskMgr.md#9800005-continuous-task-verification-failure) | Continuous task verification failed. |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    try {
      let continuousTaskRequest = new backgroundTaskManager.ContinuousTaskRequest();
      continuousTaskRequest.checkSpecialScenarioAuthResult(this.context).then((res: backgroundTaskManager.UserAuthResult) => {
        console.info('Operation checkSpecialScenarioAuthResult succeeded. data: ' + JSON.stringify(res));
      }).catch((error: BusinessError) => {
        console.error(`Operation checkSpecialScenarioAuthResult failed. code is ${error.code} message is ${error.message}`);
      });
    } catch (error) {
      console.error(`Operation checkSpecialScenarioAuthResult failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```

## isModeSupported

```TypeScript
isModeSupported(): boolean
```

Checks whether **BackgroundTaskMode** specified in [ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md) is supported. For details, see [BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md).

**Since:** 21

**Required permissions:** ohos.permission.KEEP_BACKGROUND_RUNNING

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether **BackgroundTaskMode** is supported. The value **true** means it is supported, and the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [9800005](../errorcode-backgroundTaskMgr.md#9800005-continuous-task-verification-failure) | Continuous task verification failed. |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    let isModeSupported: boolean = false; 
    let continuousTaskRequest = new backgroundTaskManager.ContinuousTaskRequest();
    let modeList: Array<number> = [backgroundTaskManager.BackgroundTaskMode.MODE_TASK_KEEPING];
    continuousTaskRequest.backgroundTaskModes = modeList;
    try {
      isModeSupported = continuousTaskRequest.isModeSupported();
      console.info(`Operation isModeSupported succeeded. isModeSupported is ${isModeSupported}`);
    } catch (error) {
      console.error(`Operation startBackgroundRunning failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```

## requestAuthFromUser

```TypeScript
requestAuthFromUser(context: Context, callback: Callback<UserAuthResult>): void
```

Requests user authorization to run tasks continuously in the background. This API uses an asynchronous callback to return the result. If the API call is successful, a banner notification with a sound is sent. This API is applicable only to continuous tasks of the [MODE_SPECIAL_SCENARIO_PROCESSING](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md) type.

**Since:** 22

**Required permissions:** ohos.permission.KEEP_BACKGROUND_RUNNING

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. <br>For details about the application context of the FA model, see Context.<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md).<br> Note: Continuous tasks can be requested only by the UIAbility in the stage model and the ServiceAbility in the FA model. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[UserAuthResult](arkts-backgroundtasks-backgroundtaskmanager-userauthresult-e.md)&gt; | Yes | Callback used to return the user authorization result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-system-service-failure) | System service operation failed. |
| [9800005](../errorcode-backgroundTaskMgr.md#9800005-continuous-task-verification-failure) | Continuous task verification failed. |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callbackAuth(authResult: backgroundTaskManager.UserAuthResult) {
  console.info('Operation requestAuthFromUser success. auth result: ' + JSON.stringify(authResult));
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    let continuousTaskRequest = new backgroundTaskManager.ContinuousTaskRequest();
    let modeList: Array<number> = [backgroundTaskManager.BackgroundTaskMode.MODE_SPECIAL_SCENARIO_PROCESSING];
    continuousTaskRequest.backgroundTaskModes = modeList;
    let subModeList: Array<number> = [backgroundTaskManager.BackgroundTaskSubmode.SUBMODE_MEDIA_PROCESS_NORMAL_NOTIFICATION];
    continuousTaskRequest.backgroundTaskSubmodes = subModeList;
    try {
      continuousTaskRequest.requestAuthFromUser(this.context, callbackAuth);
      console.info('Operation requestAuthFromUser succeeded.');
    } catch (error) {
      console.error(`Operation requestAuthFromUser failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```

## requestAuthFromUserByDialog

```TypeScript
requestAuthFromUserByDialog(context: Context, callback: Callback<UserAuthResult>): void
```

Requesting MODE_SPECIAL_SCENARIO_PROCESSING authorization from users, a dialog box will be displayed.

**Since:** 26.0.0

**Required permissions:** ohos.permission.KEEP_BACKGROUND_RUNNING

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | App running context. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[UserAuthResult](arkts-backgroundtasks-backgroundtaskmanager-userauthresult-e.md)&gt; | Yes | The callback of the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-system-service-failure) | System service operation failed. |
| [9800005](../errorcode-backgroundTaskMgr.md#9800005-continuous-task-verification-failure) | Continuous task verification failed. |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

function callbackAuth(authResult: backgroundTaskManager.UserAuthResult) {
  console.info('Operation requestAuthFromUserByDialog success. auth result: ' + JSON.stringify(authResult));
}

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        return;
      }
      try {
        let continuousTaskRequest = new backgroundTaskManager.ContinuousTaskRequest();
        let modeList: Array<number> = [backgroundTaskManager.BackgroundTaskMode.MODE_SPECIAL_SCENARIO_PROCESSING];
        continuousTaskRequest.backgroundTaskModes = modeList;
        let subModeList: Array<number> = [backgroundTaskManager.BackgroundTaskSubmode.SUBMODE_MEDIA_PROCESS_NORMAL_NOTIFICATION];
        continuousTaskRequest.backgroundTaskSubmodes = subModeList;
        continuousTaskRequest.requestAuthFromUserByDialog(this.context, callbackAuth);
        console.info('Operation requestAuthFromUserByDialog succeeded.');
      } catch (error) {
        console.error(`Operation requestAuthFromUserByDialog failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
      }
    });
  }
};
```

## backgroundTaskModes

```TypeScript
get backgroundTaskModes(): BackgroundTaskMode[]
```

Main type of a continuous task.

Note: The main type must match the subtype.

**Type:** [BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md)[]

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

```TypeScript
set backgroundTaskModes(value: BackgroundTaskMode[])
```

Main type of a continuous task.

Note: The main type must match the subtype.

**Type:** [BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md)[]

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## backgroundTaskSubmodes

```TypeScript
get backgroundTaskSubmodes(): BackgroundTaskSubmode[]
```

Subtype of a continuous task.

Note: The main type must match the subtype.

**Type:** [BackgroundTaskSubmode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubmode-e.md)[]

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

```TypeScript
set backgroundTaskSubmodes(value: BackgroundTaskSubmode[])
```

Subtype of a continuous task.

Note: The main type must match the subtype.

**Type:** [BackgroundTaskSubmode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubmode-e.md)[]

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## combinedTaskNotification

```TypeScript
combinedTaskNotification?: boolean
```

Whether to combine notifications. The value **true** means to combine notifications, and the value **false** (default) means the opposite.

Note: This property does not take effect in [updateBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md) API. If notifications need to be combined for an existing task, request the task again and set the value to **true**.

**Type:** boolean

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## continuousTaskId

```TypeScript
continuousTaskId?: number
```

Continuous task ID. The default value is **-1**.

Note: If **combinedTaskNotification** is set to true, this property is mandatory and the corresponding ID must exist.

Additionally, this property is mandatory (with the corresponding ID required) when used as an input parameter for the [updateBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md) API.

You can call the [getAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-getallcontinuoustasks-f.md) API to view information about all continuous tasks.

**Type:** number

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## progressInfo

```TypeScript
progressInfo?: ProgressInfo
```

Notify progress data.

**Type:** [ProgressInfo](arkts-backgroundtasks-backgroundtaskmanager-progressinfo-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## wantAgent

```TypeScript
get wantAgent(): WantAgent
```

Notification parameters, which are used to specify the target page that is redirected to when a continuous task notification is clicked.

**Type:** [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md)

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

```TypeScript
set wantAgent(value: WantAgent)
```

Notification parameters, which are used to specify the target page that is redirected to when a continuous task notification is clicked.

**Type:** [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md)

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
