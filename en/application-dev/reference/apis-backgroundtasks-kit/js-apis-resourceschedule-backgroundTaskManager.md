# @ohos.resourceschedule.backgroundTaskManager (Background Task Management)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @cheng-shichang-->
<!--Designer: @zhouben25-->
<!--Tester: @fenglili18-->
<!--Adviser: @Brilliantry_Rui-->

The **backgroundTaskManager** module provides APIs to request background tasks. You can use the APIs to request transient tasks, continuous tasks, or efficiency resources to prevent the application process from being terminated or suspended when your application is switched to the background.

>  **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## backgroundTaskManager.requestSuspendDelay

requestSuspendDelay(reason: string, callback: Callback&lt;void&gt;): DelaySuspendInfo

Requests a transient task.

>  **NOTE**
>
> For details about the constraints on requesting and using a transient task, see [Transient Task (ArkTS)](../../task-management/transient-task.md#constraints).

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Parameters**

| Name     | Type                  | Mandatory  | Description                            |
| -------- | -------------------- | ---- | ------------------------------ |
| reason   | string               | Yes   | Reason for requesting the transient task.                    |
| callback | Callback&lt;void&gt; | Yes   | Callback used to notify the application that the transient task is about to time out. Generally, the callback is invoked 6 seconds before the timeout.|

**Return value**

| Type                                   | Description       |
| ------------------------------------- | --------- |
| [DelaySuspendInfo](#delaysuspendinfo) | Information about the transient task.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID  | Error Message|
| --------- | ------- |
| 401    | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9800003 | Internal transaction failed. |
| 9800004 | System service operation failed. |
| 9900001 | Caller information verification failed for a transient task. |
| 9900002 | Transient task verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

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


## backgroundTaskManager.getRemainingDelayTime

getRemainingDelayTime(requestId: number, callback: AsyncCallback&lt;number&gt;): void

Obtains the remaining time of a transient task. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Parameters**

| Name      | Type                         | Mandatory  | Description                                      |
| --------- | --------------------------- | ---- | ---------------------------------------- |
| requestId | number                      | Yes   | Request ID of the transient task.                              |
| callback  | AsyncCallback&lt;number&gt; | Yes   | Callback used to return the remaining time of the transient task, in milliseconds.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID  | Error Message|
| --------- | ------- |
| 401    | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9800003 | Internal transaction failed. |
| 9800004 | System service operation failed. |
| 9900001 | Caller information verification failed for a transient task. |
| 9900002 | Transient task verification failed. |


**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let id = 1;
backgroundTaskManager.getRemainingDelayTime(id, (error: BusinessError, res: number) => {
    if(error) {
        console.error(`callback => Operation getRemainingDelayTime failed. code is ${error.code} message is ${error.message}`);
    } else {
        console.log('callback => Operation getRemainingDelayTime succeeded. Data: ' + JSON.stringify(res));
    }
})
```


## backgroundTaskManager.getRemainingDelayTime

getRemainingDelayTime(requestId: number): Promise&lt;number&gt;

Obtains the remaining time of a transient task. This API uses a promise to return the result.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Parameters**

| Name      | Type    | Mandatory  | Description        |
| --------- | ------ | ---- | ---------- |
| requestId | number | Yes   | Request ID of the transient task.|

**Return value**

| Type                   | Description                                      |
| --------------------- | ---------------------------------------- |
| Promise&lt;number&gt; | Promise that returns the remaining time of the transient task, in milliseconds.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID  | Error Message|
| --------- | ------- |
| 401    | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9800003 | Internal transaction failed. |
| 9800004 | System service operation failed. |
| 9900001 | Caller information verification failed for a transient task. |
| 9900002 | Transient task verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let id = 1;
backgroundTaskManager.getRemainingDelayTime(id).then((res: number) => {
    console.log('promise => Operation getRemainingDelayTime succeeded. Data: ' + JSON.stringify(res));
}).catch((error: BusinessError) => {
    console.error(`promise => Operation getRemainingDelayTime failed. code is ${error.code} message is ${error.message}`);
})
```


## backgroundTaskManager.cancelSuspendDelay

cancelSuspendDelay(requestId: number): void

Cancels a transient task.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Parameters**

| Name      | Type    | Mandatory  | Description        |
| --------- | ------ | ---- | ---------- |
| requestId | number | Yes   | Request ID of the transient task.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID  | Error Message|
| --------- | ------- |
| 401    | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9800003 | Internal transaction failed. |
| 9800004 | System service operation failed. |
| 9900001 | Caller information verification failed for a transient task. |
| 9900002 | Transient task verification failed. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';

  let id = 1;
  try {
    backgroundTaskManager.cancelSuspendDelay(id);
  } catch (error) {
    console.error(`cancelSuspendDelay failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
  }
  ```

## backgroundTaskManager.getTransientTaskInfo<sup>20+</sup>

getTransientTaskInfo(): Promise&lt;TransientTaskInfo&gt;

Obtains all transient task information, including the remaining quota of the current day. This API uses a promise to return the result.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Return value**

| Type                                     | Description         |
|-----------------------------------------|-------------|
|  Promise&lt;[TransientTaskInfo](#transienttaskinfo20)&gt; | Promise that returns all transient task information.|

**Error codes**

For details about the error codes, see [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID  | Error Message|
| --------- | ------- |
| 9900001 | Caller information verification failed for a transient task. |
| 9900003 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9900004 | System service operation failed. |

**Example**

```ts
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

## backgroundTaskManager.startBackgroundRunning

startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback&lt;void&gt;): void

Requests a continuous task of a specific type. This API uses an asynchronous callback to return the result. After a continuous task is successfully requested, there will be a notification message without prompt tone.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name      | Type                                | Mandatory  | Description                                      |
| --------- | ---------------------------------- | ---- | ---------------------------------------- |
| context   | Context                            | Yes   | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| bgMode    | [BackgroundMode](#backgroundmode) | Yes   | Type of the continuous task.                          |
| wantAgent | [WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md) | Yes   | Notification parameters, which are used to specify the target page that is redirected to when a continuous task notification is clicked.          |
| callback  | AsyncCallback&lt;void&gt;          | Yes   | Callback used to return the result. If the continuous task is requested, **err** is **undefined**. Otherwise, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201 | Permission denied. |
| 202 | Not System App. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9800003 | Internal transaction failed. |
| 9800004 | System service operation failed. |
| 9800005 | Continuous task verification failed. |
| 9800006 | Notification verification failed for a continuous task. |
| 9800007 | Continuous task storage failed. |

**Example**

```js
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { wantAgent, WantAgent } from '@kit.AbilityKit';
// In atomic services, please remove the WantAgent import.

function callback(error: BusinessError, data: void) {
    if (error) {
        console.error(`Operation startBackgroundRunning failed. code is ${error.code} message is ${error.message}`);
    } else {
        console.info("Operation startBackgroundRunning succeeded");
    }
}

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        let wantAgentInfo: wantAgent.WantAgentInfo = {
            // List of operations to be executed after the notification is clicked.
            wants: [
                {
                    bundleName: "com.example.myapplication",
                    abilityName: "EntryAbility"
                }
            ],
            // Type of the operation to perform after the notification is clicked.
            actionType: wantAgent.OperationType.START_ABILITY,
            // Custom request code.
            requestCode: 0,
            // Execution attribute of the operation to perform after the notification is clicked.
            wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
        };

        try {
            // Obtain the WantAgent object by using the getWantAgent API of the wantAgent module.
            // In atomic services, please replace the following line of code with wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: object) => {.
            wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: WantAgent) => {
                try {
                    backgroundTaskManager.startBackgroundRunning(this.context,
                        backgroundTaskManager.BackgroundMode.AUDIO_PLAYBACK, wantAgentObj, callback)
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

## backgroundTaskManager.startBackgroundRunning

startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise&lt;void&gt;

Requests a continuous task of a specific type. This API uses a promise to return the result. After a continuous task is successfully requested, there will be a notification message without prompt tone.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name      | Type                                | Mandatory  | Description                                      |
| --------- | ---------------------------------- | ---- | ---------------------------------------- |
| context   | Context                            | Yes   | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| bgMode    | [BackgroundMode](#backgroundmode) | Yes   | Type of the continuous task.                         |
| wantAgent | [WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md) | Yes   | Notification parameters, which are used to specify the target page that is redirected to when a continuous task notification is clicked.                |

**Return value**

| Type            | Description              |
| -------------- | ---------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201 | Permission denied. |
| 202 | Not System App. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9800003 | Internal transaction failed. |
| 9800004 | System service operation failed. |
| 9800005 | Continuous task verification failed. |
| 9800006 | Notification verification failed for a continuous task. |
| 9800007 | Continuous task storage failed. |

**Example**

```js
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { wantAgent, WantAgent } from '@kit.AbilityKit';
// In atomic services, please remove the WantAgent import.

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        let wantAgentInfo: wantAgent.WantAgentInfo = {
            // List of operations to be executed after the notification is clicked.
            wants: [
                {
                    bundleName: "com.example.myapplication",
                    abilityName: "EntryAbility"
                }
            ],
            // Type of the operation to perform after the notification is clicked.
            actionType: wantAgent.OperationType.START_ABILITY,
            // Custom request code.
            requestCode: 0,
            // Execution attribute of the operation to perform after the notification is clicked.
            wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
        };

        try {
            // Obtain the WantAgent object by using the getWantAgent API of the wantAgent module.
            // In atomic services, please replace the following line of code with wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: object) => {.
            wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: WantAgent) => {
                try {
                    backgroundTaskManager.startBackgroundRunning(this.context,
                        backgroundTaskManager.BackgroundMode.AUDIO_PLAYBACK, wantAgentObj).then(() => {
                        console.info("Operation startBackgroundRunning succeeded");
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

## backgroundTaskManager.stopBackgroundRunning

stopBackgroundRunning(context: Context, callback: AsyncCallback&lt;void&gt;): void

Cancels a continuous task. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name     | Type                       | Mandatory  | Description                                      |
| -------- | ------------------------- | ---- | ---------------------------------------- |
| context  | Context                   | Yes   | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the continuous task is canceled, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9800003 | Internal transaction failed. |
| 9800004 | System service operation failed. |
| 9800005 | Continuous task verification failed. |
| 9800006 | Notification verification failed for a continuous task. |
| 9800007 | Continuous task storage failed. |

**Example**

```js
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

## backgroundTaskManager.stopBackgroundRunning

stopBackgroundRunning(context: Context): Promise&lt;void&gt;

Cancels a continuous task. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name    | Type     | Mandatory  | Description                                      |
| ------- | ------- | ---- | ---------------------------------------- |
| context | Context | Yes   | Application context.<br>For details about the application context of the FA model, see [Context](../apis-ability-kit/js-apis-inner-app-context.md).<br>For details about the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|

**Return value**

| Type            | Description              |
| -------------- | ---------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9800003 | Internal transaction failed. |
| 9800004 | System service operation failed. |
| 9800005 | Continuous task verification failed. |
| 9800006 | Notification verification failed for a continuous task. |
| 9800007 | Continuous task storage failed. |

**Example**

```js
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

## backgroundTaskManager.startBackgroundRunning<sup>12+</sup>

startBackgroundRunning(context: Context, bgModes: string[], wantAgent: WantAgent): Promise&lt;ContinuousTaskNotification&gt;

Requests continuous tasks of multiple types. This API uses a promise to return the result. After a continuous task is successfully requested, there will be a notification message without prompt tone.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name      | Type                                | Mandatory  | Description                                      |
| --------- | ---------------------------------- | ---- | ---------------------------------------- |
| context   | [Context](../apis-ability-kit/js-apis-inner-application-context.md)                            | Yes   | Application context.|
| bgModes    | string[] | Yes   | Types of continuous tasks. For details about the available options, see [Item](../../task-management/continuous-task.md#use-cases).<br> **Note**: One or more types can be passed.|
| wantAgent | [WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md) | Yes   | Notification parameters, which are used to specify the target page that is redirected to when a continuous task notification is clicked.                |

**Return value**

| Type            | Description              |
| -------------- | ---------------- |
| Promise\<ContinuousTaskNotification> | Promise that returns an object of the [ContinuousTaskNotification](#continuoustasknotification12) type.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9800003 | Internal transaction failed. |
| 9800004 | System service operation failed. |
| 9800005 | Continuous task verification failed. |
| 9800006 | Notification verification failed for a continuous task. |
| 9800007 | Continuous task storage failed. |

**Example**

```js
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationManager } from '@kit.NotificationKit';
import { wantAgent, WantAgent } from '@kit.AbilityKit';
// In atomic services, please remove the WantAgent import.

export default class EntryAbility extends UIAbility {
  id: number = 0; // Save the notification ID.

  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      // List of operations to be executed after the notification is clicked.
      wants: [
        {
          bundleName: "com.example.myapplication",
          abilityName: "EntryAbility"
        }
      ],
      // Type of the operation to perform after the notification is clicked.
      actionType: wantAgent.OperationType.START_ABILITY,
      // Custom request code.
      requestCode: 0,
      // Execution attribute of the operation to perform after the notification is clicked.
      wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
    };

    try {
      // Obtain the WantAgent object by using the getWantAgent API of the wantAgent module.
      // In atomic services, please replace the following line of code with wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: object) => {.
      wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: WantAgent) => {
        try {
          let list: Array<string> = ["dataTransfer"];
          // In atomic services, let list: Array<string> = ["audioPlayback"];
          backgroundTaskManager.startBackgroundRunning(this.context, list, wantAgentObj).then((res: backgroundTaskManager.ContinuousTaskNotification) => {
            console.info("Operation startBackgroundRunning succeeded");
            // For a continuous task of the upload and download type, the application can use the notification ID returned in res to update the notification, for example, sending a template notification with a progress bar.
            this.id = res.notificationId;
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

  // The application updates its progress.
  updateProcess(process: number) {
    // The application defines the download notification template.
    let downLoadTemplate: notificationManager.NotificationTemplate = {
      name: 'downloadTemplate', // Currently, only downloadTemplate is supported. Retain the value.
      data: {
        title: 'File download: music.mp4', // Mandatory.
        fileName: 'senTemplate', // Mandatory.
        progressValue: process, // The application updates the progress, which is user-defined.
      }
    };
    let request: notificationManager.NotificationRequest = {
      content: {
        // System live view type, which remains unchanged.
        notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_SYSTEM_LIVE_VIEW,
        systemLiveView: {
          typeCode: 8, // Set this parameter to 8 for the upload and download type. Currently, only the upload and download type is supported. Retain the value.
          title: "test", // Customized by the application.
          text: "test", // Customized by the application.
        }
      },
      id: this.id, // The value must be the ID returned for a continuous-task request. Otherwise, the application fails to update the notification.
      notificationSlotType: notificationManager.SlotType.LIVE_VIEW, // Live view type. Retain the value.
      template: downLoadTemplate // Name of the template to be set for the application.
    };

    try {
      notificationManager.publish(request).then(() => {
        console.info("publish success, id= " + this.id);
      }).catch((err: BusinessError) => {
        console.error(`publish fail: ${JSON.stringify(err)}`);
      });
    } catch (err) {
      console.error(`publish fail: ${JSON.stringify(err)}`);
    }
  }
};
```

## backgroundTaskManager.updateBackgroundRunning<sup>12+</sup>

updateBackgroundRunning(context: Context, bgModes: string[]): Promise&lt;ContinuousTaskNotification&gt;

Updates continuous tasks of multiple types. This API uses a promise to return the result. After a continuous task is successfully updated, there will be a notification message without prompt tone.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name      | Type                                | Mandatory  | Description                                      |
| --------- | ---------------------------------- | ---- | ---------------------------------------- |
| context   | [Context](../apis-ability-kit/js-apis-inner-application-context.md)                            | Yes   | Application context.|
| bgModes    | string[] | Yes   | Types of continuous tasks after the update. For details about the available options, see [Item](../../task-management/continuous-task.md#use-cases).<br> **Note**: One or more types can be passed.|

**Return value**

| Type            | Description              |
| -------------- | ---------------- |
| Promise\<ContinuousTaskNotification> | Promise that returns an object of the [ContinuousTaskNotification](#continuoustasknotification12) type.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9800003 | Internal transaction failed. |
| 9800004 | System service operation failed. |
| 9800005 | Continuous task verification failed. |
| 9800006 | Notification verification failed for a continuous task. |
| 9800007 | Continuous task storage failed. |

**Example**

```js
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

## backgroundTaskManager.getAllContinuousTasks<sup>20+</sup>

getAllContinuousTasks(context: Context): Promise&lt;ContinuousTaskInfo[]&gt;

Obtains all continuous task information, including the task ID and type. This API uses a promise to return the result.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name      | Type                                | Mandatory  | Description                                      |
| --------- | ---------------------------------- | ---- | ---------------------------------------- |
| context   | [Context](../apis-ability-kit/js-apis-inner-application-context.md)                            | Yes   | Application context.|

**Return value**

| Type                                           | Description         |
|-----------------------------------------------|-------------|
|  Promise&lt;[ContinuousTaskInfo](#continuoustaskinfo20)[]&gt; | Promise that returns all continuous task information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID  | Error Message|
| --------- | ------- |
| 201 | Permission denied. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9800004 | System service operation failed. |
| 9800005 | Continuous task verification failed. |

**Example**

```ts
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        try {
            // If no continuous task is requested, an empty array is obtained.
            backgroundTaskManager.getAllContinuousTasks(this.context).then((res: backgroundTaskManager.ContinuousTaskInfo[]) => {
                console.info(`Operation getAllContinuousTasks succeeded. data: ` + JSON.stringify(res));
            }).catch((error: BusinessError) => {
                console.error(`Operation getAllContinuousTasks failed. code is ${error.code} message is ${error.message}`);
            });
        } catch (error) {
            console.error(`Operation getAllContinuousTasks failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
    }
};
```

## backgroundTaskManager.on('continuousTaskCancel')<sup>15+</sup>

on(type: 'continuousTaskCancel', callback: Callback&lt;ContinuousTaskCancelInfo&gt;): void

Subscribes to continuous task cancellation events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name      | Type                                | Mandatory  | Description                                      |
| --------- | ---------------------------------- | ---- | ---------------------------------------- |
| type   | string                            | Yes   | Cancels a continuous task. The value is fixed at **'continuousTaskCancel'**.|
| callback   | Callback\<[ContinuousTaskCancelInfo](#continuoustaskcancelinfo15)>       | Yes   | Callback used to return information such as the reason for canceling a continuous task.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible cause: 1. Callback parameter error; 2. Register a exist callback type; 3. Parameter verification failed. |

**Example**

```js
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

function callback(info: backgroundTaskManager.ContinuousTaskCancelInfo) {
  console.info('continuousTaskCancel callback id ' + info.id);
  console.info('continuousTaskCancel callback reason ' + info.reason);
}

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        try {
            backgroundTaskManager.on("continuousTaskCancel", callback);
        } catch (error) {
            console.error(`Operation onContinuousTaskCancel failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
    }
};
```
## backgroundTaskManager.off('continuousTaskCancel')<sup>15+</sup>

off(type: 'continuousTaskCancel', callback?: Callback&lt;ContinuousTaskCancelInfo&gt;): void

Unsubscribes from continuous task cancellation events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name      | Type                                | Mandatory  | Description                                      |
| --------- | ---------------------------------- | ---- | ---------------------------------------- |
| type   | string                            | Yes   | Cancels a continuous task. The value is fixed at **'continuousTaskCancel'**.|
| callback   | Callback\<[ContinuousTaskCancelInfo](#continuoustaskcancelinfo15)>       | No   | Callback for which listening is cancelled. If this parameter is left unspecified, all registered callbacks are cancelled.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible cause: 1. Callback parameter error; 2. Unregister type has not register; 3. Parameter verification failed. |

**Example**

```js
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

function callback(info: backgroundTaskManager.ContinuousTaskCancelInfo) {
  console.info('continuousTaskCancel callback id ' + info.id);
  console.info('continuousTaskCancel callback reason ' + info.reason);
}

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        try {
            backgroundTaskManager.off("continuousTaskCancel", callback);
        } catch (error) {
            console.error(`Operation onContinuousTaskCancel failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
    }
};
```
## backgroundTaskManager.on('continuousTaskSuspend')<sup>20+</sup>

on(type: 'continuousTaskSuspend', callback: Callback&lt;ContinuousTaskSuspendInfo&gt;): void

Registers a listener for continuous task suspension. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name      | Type                                | Mandatory  | Description                                      |
| --------- | ---------------------------------- | ---- | ---------------------------------------- |
| type   | string                            | Yes   | Event type. The value is fixed at **'continuousTaskSuspend'**, indicating that the continuous task is suspended.|
| callback   | Callback\<[ContinuousTaskSuspendInfo](#continuoustasksuspendinfo20)>       | Yes   | Callback used to return information such as the reason for suspending the continuous task.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201 | Permission denied. |
| 9800005 | Continuous task verification failed. |

**Example**


```js
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

function callback(info: backgroundTaskManager.ContinuousTaskSuspendInfo) {
  console.info('continuousTaskSuspend callback continuousTaskId: ' + info.continuousTaskId);
  console.info('continuousTaskSuspend callback suspendState: ' + info.suspendState);
  console.info('continuousTaskSuspend callback suspendReason: ' + info.suspendReason);
}

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        try {
            backgroundTaskManager.on("continuousTaskSuspend", callback);
        } catch (error) {
            console.error(`Operation onContinuousTaskSuspend failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
    }
};
```
## backgroundTaskManager.off('continuousTaskSuspend')<sup>20+</sup>

off(type: 'continuousTaskSuspend', callback?: Callback&lt;ContinuousTaskSuspendInfo&gt;): void

Unregisters from the listener for continuous task suspension. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name      | Type                                | Mandatory  | Description                                      |
| --------- | ---------------------------------- | ---- | ---------------------------------------- |
| type   | string                            | Yes   | Event type. The value is fixed at **'continuousTaskSuspend'**, indicating that the continuous task is suspended.|
| callback   | Callback\<[ContinuousTaskSuspendInfo](#continuoustasksuspendinfo20)>       | No   | Callback used to unregister from the listener for continuous task suspension. If this parameter is not passed, all listeners are unsubscribed from.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201 | Permission denied. |
| 9800005 | Continuous task verification failed. |

**Example**

```js
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

function callback(info: backgroundTaskManager.ContinuousTaskSuspendInfo) {
  console.info('continuousTaskSuspend callback continuousTaskId: ' + info.continuousTaskId);
  console.info('continuousTaskSuspend callback suspendState: ' + info.suspendState);
  console.info('continuousTaskSuspend callback suspendReason: ' + info.suspendReason);
}

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        try {
            backgroundTaskManager.off("continuousTaskSuspend", callback);
        } catch (error) {
            console.error(`Operation offContinuousTaskSuspend failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
    }
};
```
## backgroundTaskManager.on('continuousTaskActive')<sup>20+</sup>

on(type: 'continuousTaskActive', callback: Callback&lt;ContinuousTaskActiveInfo&gt;): void

Registers a listener for continuous task activation. This API uses an asynchronous callback to return the result. The application returns to the foreground to activate the suspended continuous task.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name      | Type                                | Mandatory  | Description                                      |
| --------- | ---------------------------------- | ---- | ---------------------------------------- |
| type   | string                            | Yes   | Event type. The value is fixed at **'continuousTaskActive'**, indicating that the continuous task is activated.|
| callback   | Callback\<[ContinuousTaskActiveInfo](#continuoustaskactiveinfo20)>       | Yes   | Callback used to return the activation information about a continuous task.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201 | Permission denied. |
| 9800005 | Continuous task verification failed. |

**Example**

```js
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

function callback(info: backgroundTaskManager.ContinuousTaskActiveInfo) {
  console.info('continuousTaskActive callback id: ' + info.id);
}

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        try {
            backgroundTaskManager.on("continuousTaskActive", callback);
        } catch (error) {
            console.error(`Operation onContinuousTaskActive failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
    }
};
```
## backgroundTaskManager.off('continuousTaskActive')<sup>20+</sup>

off(type: 'continuousTaskActive', callback?: Callback&lt;ContinuousTaskActiveInfo&gt;): void

Unregisters from the listener for continuous task activation. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name      | Type                                | Mandatory  | Description                                      |
| --------- | ---------------------------------- | ---- | ---------------------------------------- |
| type   | string                            | Yes   | Event type. The value is fixed at **'continuousTaskActive'**, indicating that the continuous task is activated.|
| callback   | Callback\<[ContinuousTaskActiveInfo](#continuoustaskactiveinfo20)>       | No   | Callback used to unregister from the listener for continuous task activation. If this parameter is not passed, all listeners are unsubscribed from.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201 | Permission denied. |
| 9800005 | Continuous task verification failed. |

**Example**

```js
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

function callback(info: backgroundTaskManager.ContinuousTaskActiveInfo) {
  console.info('continuousTaskActive callback id: ' + info.id);
}

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        try {
            backgroundTaskManager.off("continuousTaskActive", callback);
        } catch (error) {
            console.error(`Operation offContinuousTaskActive failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
    }
};
```

## DelaySuspendInfo

Defines the information about the transient task.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

| Name            | Type    | Read-Only  | Optional  | Description                                      |
| --------------- | ------ | ---- | ---- | ---------------------------------------- |
| requestId       | number | No   | No   | Request ID of the transient task.                              |
| actualDelayTime | number | No   | No   | Actual duration of the transient task requested by the application, in milliseconds.<br> **Note**: The maximum duration is 3 minutes in normal cases. In the case of a [low battery](../apis-basic-services-kit/js-apis-battery-info.md), the maximum duration is decreased to 1 minute.|

## TransientTaskInfo<sup>20+</sup>

Describes all transient task information.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

| Name            | Type                                     | Read-Only  | Optional  | Description             |
| --------------- |-----------------------------------------| ---- | ---- |-----------------|
| remainingQuota       | number                                  | No   | No   | Remaining quota of the application on the current day, in ms.    |
| transientTasks | [DelaySuspendInfo](#delaysuspendinfo)[] | No   | No   | All information about the requested transient task.|

## BackgroundMode

Type of the continuous task.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

| Name                    | Value | Description                   |
| ----------------------- | ---- | --------------------- |
| DATA_TRANSFER           | 1    | Data transfer.                 |
| AUDIO_PLAYBACK          | 2    | Audio and video playback.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                 |
| AUDIO_RECORDING         | 3    | Audio recording.                   |
| LOCATION                | 4    | Positioning and navigation.                 |
| BLUETOOTH_INTERACTION   | 5    | Bluetooth-related services.                 |
| MULTI_DEVICE_CONNECTION | 6    | Multi-device connection.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                |
| VOIP<sup>13+</sup> | 8    | Audio and video calls.                |
| TASK_KEEPING            | 9    | Computing task (for 2-in-1 devices only).       |

## ContinuousTaskNotification<sup>12+</sup>

Describes the information about a continuous-task notification.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

| Name            | Type    | Read-Only    | Optional  | Description                                      |
| --------------- | ------ | ---- | ---- | ---------------------------------------- |
| slotType       | [notificationManager.SlotType](../apis-notification-kit/js-apis-notificationManager.md#slottype) | No   | No   | Slot type of a continuous-task notification.<br>**Note**: After a continuous task is successfully requested or updated, no prompt tone is played.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| contentType | [notificationManager.ContentType](../apis-notification-kit/js-apis-notificationManager.md#contenttype) | No   | No   | Content type of a continuous-task notification.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| notificationId | number | No   | No   | ID of the continuous-task notification.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| continuousTaskId<sup>15+</sup> | number | No   | Yes   | ID of a continuous task|

## ContinuousTaskCancelInfo<sup>15+</sup>

Describes the information about the cancellation of a continuous task.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

| Name            | Type    | Read-Only  | Optional  | Description                                      |
| --------------- | ------ | ---- | ---- | ---------------------------------------- |
| reason | [ContinuousTaskCancelReason](#continuoustaskcancelreason15) | No   | No   | Reason for canceling the continuous task.|
| id | number | No   | No   | ID of the continuous task canceled.|

## ContinuousTaskCancelReason<sup>15+</sup>

Describes the reason for canceling a continuous task.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

| Name                    | Value | Description                   |
| ----------------------- | ---- | --------------------- |
| USER_CANCEL             | 1    | The task is canceled by the user.                 |
| SYSTEM_CANCEL           | 2    | The task is canceled by the system.                 |
| USER_CANCEL_REMOVE_NOTIFICATION         | 3    | User removal notification. This value is reserved.                   |
| SYSTEM_CANCEL_DATA_TRANSFER_LOW_SPEED                | 4    | A continuous task of the DATA_TRANSFER type is requested, but the data transmission rate is low. This value is reserved.                 |
| SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_USE_AVSESSION   | 5    | A continuous task of the AUDIO_PLAYBACK type is requested, but the [AVSession](../../media/avsession/avsession-overview.md) is not accessed. This value is reserved.                 |
| SYSTEM_CANCEL_AUDIO_PLAYBACK_NOT_RUNNING | 6    | A continuous task of the AUDIO_PLAYBACK type is requested, but the audio and video are not played. This value is reserved.                |
| SYSTEM_CANCEL_AUDIO_RECORDING_NOT_RUNNING | 7    | A continuous task of the AUDIO_RECORDING type is requested, but audio recording is not in progress. This value is reserved.                |
| SYSTEM_CANCEL_NOT_USE_LOCATION            | 8    | A continuous task of the LOCATION type is requested, but location and navigation are not used. This value is reserved.       |
| SYSTEM_CANCEL_NOT_USE_BLUETOOTH            | 9    | A continuous task of the BLUETOOTH_INTERACTION type is requested, but Bluetooth-related services are not used. This value is reserved.       |
| SYSTEM_CANCEL_NOT_USE_MULTI_DEVICE            | 10    | A continuous task of the MULTI_DEVICE_CONNECTION type is requested, but multi-device connection is not used. This value is reserved.       |
| SYSTEM_CANCEL_USE_ILLEGALLY            | 11    | A continuous task of an invalid type is used. For example, a continuous task of the AUDIO_PLAYBACK type is requested, but the audio and video playback and location and navigation services are used. This value is reserved.       |

## BackgroundSubMode<sup>16+</sup>

Subtype of a continuous task.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

| Name                    | Value | Description                   |
| ----------------------- | ---- | --------------------- |
| CAR_KEY           | 1    | Car key.<br>Note: The car key subtype takes effect only when a continuous task of the BLUETOOTH_INTERACTION type is requested.                 |

## BackgroundModeType<sup>16+</sup>

Type of a continuous task.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

| Name                    | Value | Description                   |
| ----------------------- | ---- | --------------------- |
| SUB_MODE           | 'subMode'    | Subtype.                 |

## ContinuousTaskSuspendInfo<sup>20+</sup>

Describes the information about continuous task suspension.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

| Name            | Type    | Read-Only  | Optional  | Description                                      |
| --------------- | ------ | ---- | ---- | ---------------------------------------- |
| continuousTaskId | number | No   | No   | ID of a suspended continuous task.|
| suspendState | boolean | No   | No   | Continuous task state. The value **false** indicates that the task is activated, and the value **true** indicates that the task is suspended.|
| suspendReason | [ContinuousTaskSuspendReason](#continuoustasksuspendreason20) | No   | No   | Reason why the continuous task is suspended.|

## ContinuousTaskSuspendReason<sup>20+</sup>

Describes the reason why the continuous task is suspended.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

| Name                    | Value | Description                   |
| ----------------------- | ---- | --------------------- |
| SYSTEM_SUSPEND_DATA_TRANSFER_LOW_SPEED     | 4    | A continuous task of the DATA_TRANSFER type is requested, but the data transmission rate is low.                |
| SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_USE_AVSESSION   | 5    | A continuous task of the AUDIO_PLAYBACK type is requested, but the [AVSession](../../media/avsession/avsession-overview.md) is not accessed.                 |
| SYSTEM_SUSPEND_AUDIO_PLAYBACK_NOT_RUNNING  | 6    | A continuous task of the AUDIO_PLAYBACK type is requested, but the audio and video are not played. |
| SYSTEM_SUSPEND_AUDIO_RECORDING_NOT_RUNNING | 7    | A continuous task of the AUDIO_RECORDING type is requested, but audio recording is not in progress. |
| SYSTEM_SUSPEND_LOCATION_NOT_USED           | 8    | A continuous task of the LOCATION type is requested, but location and navigation are not used.|
| SYSTEM_SUSPEND_BLUETOOTH_NOT_USED          | 9    | A continuous task of the BLUETOOTH_INTERACTION type is requested, but Bluetooth-related services are not used.|
| SYSTEM_SUSPEND_MULTI_DEVICE_NOT_USED       | 10   | A continuous task of the MULTI_DEVICE_CONNECTION type is requested, but multi-device connection is not used. |
| SYSTEM_SUSPEND_USED_ILLEGALLY              | 11    | A continuous task of an invalid type is used. For example, a continuous task of the AUDIO_PLAYBACK type is requested, but the audio and video playback and location and navigation services are used. This value is reserved.       |
| SYSTEM_SUSPEND_SYSTEM_LOAD_WARNING         | 12    | A continuous task is suspended due to high system load. This value is reserved.       |

## ContinuousTaskActiveInfo<sup>20+</sup>

Describes the activation information of a continuous task.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

| Name            | Type    | Read-Only  | Optional  | Description                                      |
| --------------- | ------ | ---- | ---- | ---------------------------------------- |
| id | number | No   | No   | ID of the activated continuous task.|

## ContinuousTaskInfo<sup>20+</sup>

Describes the continuous task information.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

| Name         | Type      | Read-Only  | Optional  | Description                   |
|-------------|----------| ---- | ---- |-----------------------|
| abilityName | string   | No   | No   | UIAbility name.         |
| uid         | number   | No   | No   | Application UID.              |
| pid         | number   | No   | No   | Application PID.              |
| isFromWebView | boolean  | No   | No   | Whether to request a continuous task in WebView mode, that is, whether to request a continuous task through the system proxy application.     |
| [backgroundModes](#backgroundmode) | string[] | No   | No   | Type of the continuous task.              |
| [backgroundSubModes](#backgroundsubmode16) | string[] | No   | No   | Subtype of a continuous task.             |
| notificationId | number   | No   | No   | Notification ID.               |
| continuousTaskId | number   | No   | No   | ID of a continuous task.             |
| abilityId | number   | No   | No   | UIAbility ID.        |
| wantAgentBundleName | string   | No   | No   | Bundle name configured for **WantAgent**, a notification parameter used to specify the target page when a continuous task notification is tapped.       |
| wantAgentAbilityName | string   | No   | No   | Ability name configured for **WantAgent**, a notification parameter used to specify the target page when a continuous task notification is tapped.|
