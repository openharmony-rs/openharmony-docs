# stopBackgroundRunning

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## stopBackgroundRunning

```TypeScript
function stopBackgroundRunning(context: Context, callback: AsyncCallback<void>): void
```

Cancels all continuous tasks in the current UIAbility (ServiceAbility in the FA model). This API uses an asynchronous callback to return the result. You can also call the [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md) API to cancel a continuous task with the specified ID.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. <br>For details about the application context of the FA model, see Context.<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md).<br> Note: Continuous tasks can be requested only by the UIAbility in the stage model and the ServiceAbility in the FA model. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the continuous task is canceled, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 9 - 18 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
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

function callback(error: BusinessError, data: void) {
  if (error) {
    console.error(`Operation stopBackgroundRunning failed. code is ${error.code} message is ${error.message}`);
  } else {
    console.info("Operation stopBackgroundRunning succeeded");
  }
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    try {
      backgroundTaskManager.stopBackgroundRunning(this.context, callback);
    } catch (error) {
      console.error(`Operation stopBackgroundRunning failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```


<a id="stopbackgroundrunning-1"></a>

## stopBackgroundRunning

```TypeScript
function stopBackgroundRunning(context: Context): Promise<void>
```

Cancels all continuous tasks in the current UIAbility (ServiceAbility in the FA model). This API uses a promise to return the result. You can also call the [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md) API to cancel a continuous task with the specified ID.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. <br>For details about the application context of the FA model, see Context.<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md).<br> Note: Continuous tasks can be requested only by the UIAbility in the stage model and the ServiceAbility in the FA model. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 9 - 18 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
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
      backgroundTaskManager.stopBackgroundRunning(this.context).then(() => {
        console.info("Operation stopBackgroundRunning succeeded");
      }).catch((error: BusinessError) => {
        console.error(`Operation stopBackgroundRunning failed. code is ${error.code} message is ${error.message}`);
      });
    } catch (error) {
      console.error(`Operation stopBackgroundRunning failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```


<a id="stopbackgroundrunning-2"></a>

## stopBackgroundRunning

```TypeScript
function stopBackgroundRunning(context: Context, continuousTaskId: number): Promise<void>
```

Cancels a continuous task with the specified ID. This API uses a promise to return the result. You can also call the [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md) API to cancel all continuous tasks in the current UIAbility.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. <br>For details about the application context of the FA model, see Context.<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md).<br> Note: Continuous tasks can be requested only by the UIAbility in the stage model and the ServiceAbility in the FA model. |
| continuousTaskId | number | Yes | Continuous task ID. <br>The value should be an integer. <br>Note: You can obtain the ID of the current continuous task through the return value of the [startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-3) API, or obtain information about all continuous tasks through the [getAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-getallcontinuoustasks-f.md#getallcontinuoustasks-1) API. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9800001](../errorcode-backgroundTaskMgr.md#9800001-memory-operation-failure) | Memory operation failed. |
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
  continuousTaskId: number = 0;
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    try {
      backgroundTaskManager.stopBackgroundRunning(this.context, this.continuousTaskId).then(() => {
        console.info("Operation stopBackgroundRunning succeeded");
      }).catch((error: BusinessError) => {
        console.error(`Operation stopBackgroundRunning failed. code is ${error.code} message is ${error.message}`);
      });
    } catch (error) {
      console.error(`Operation stopBackgroundRunning failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```
