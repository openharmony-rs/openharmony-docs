# @ohos.resourceschedule.backgroundLoader (Background Loader)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=90c584b519a94e004e725c08133277003ce9030e translatedAt=2026-11-03T03:29:01.507Z pushedAt=2026-11-03T06:42:52.073Z nl=1 -->

This module supports the registration, unregistration, query, and completion notification of background loading tasks. During development, if you need to preload app data to improve the app startup speed, you can call the APIs provided by this module to register a background loading task. The system intelligently schedules and executes the task during idle periods by taking into account factors such as the current memory usage, remaining battery level, and device temperature. For the development guide, see [Deferred Task (ArkTS)](../../task-management/work-scheduler.md).

**Since:** 26.1.0

## Modules to Import

```ts
import { backgroundLoader } from '@kit.BackgroundTasksKit';
```
## Constants

The constants provided by this module are used to identify the callback method types of background loading tasks. Applications use these constants to register callback methods with the system.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**System API**: This is a system API.

| Name | Type | Value | Description |
| -------- | -------- | -------- | -------- |
| ON_START | string | 'onStart' | The app needs to implement the onStart callback method of the background loading task, in which the loading logic for processing app page data in the background is implemented. The app needs to use ON_START as the method name to register the callback method with the system through Callee. The system invokes the callback through Caller. For details about the Callee/Caller callback mechanism, see [Callee](../apis-ability-kit/js-apis-app-ability-uiAbility.md#callee). For the code example, see the full instance of the [finishTask](#backgroundloaderfinishtask) function. |
| ON_STOP | string | 'onStop' | The app needs to implement the onStop callback method of the background loading task to handle the case where the background loading task is terminated abnormally. The app needs to use ON_STOP as the method name to register the callback method with the system through Callee. The system invokes the callback through Caller. For details about the Callee/Caller callback mechanism, see [Callee](../apis-ability-kit/js-apis-app-ability-uiAbility.md#callee). For the code example, see the full instance of the [finishTask](#backgroundloaderfinishtask) function. |

## backgroundLoader.registerTask

registerTask(taskInfo: TaskInfo): void

Registers a background loading task. After successful registration, the task is added to the background loading task queue, and the system schedules and executes the task when the trigger conditions are met. Registering the same task multiple times overwrites the previous task, and only the last registration takes effect.

**Since:** 26.1.0

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**Model restriction**: This API can be used only in the stage model.

**Parameters**
| Name | Type | Mandatory | Description |
| ---- | --------------------- | ---- | -------------- |
| taskInfo | [TaskInfo](#taskinfo) | Yes | Specific information of the specified background loading task, including the task ID and target AbilityName. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [workScheduler Error Codes](errorcode-workScheduler.md).

| ID  | Error Message             |
| ---- | --------------------- |
| 201 | No permission. |
| 9700003 | System service operation failed. |
| 9700004 | Check on taskInfo failed. |

**Example**

```ts
  import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';
  import { backgroundLoader } from '@kit.BackgroundTasksKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  export default class TestAppMainUIAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        console.info('Callee onCreate is called');
        try {

            // 01. Define the parameters of the background loading task.
            let taskInfo: backgroundLoader.TaskInfo = {
                taskId: 1,
                abilityName: 'TestAppMainUIAbility'
            }

            // 02. Register and start the background loading task. The system persists the task record for subsequent scheduling.
            backgroundLoader.registerTask(taskInfo);
            console.info('registerTask success');
        } catch (error) {
            console.error(`backgroundLoader.registerTask catch error, code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
    }
  }
```

## backgroundLoader.unregisterTask

unregisterTask(taskInfo: TaskInfo): void

Unregisters the background loading task.

**Since:** 26.1.0

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**Model restriction**: This API can be used only in the stage model.

**Parameters**
| Name | Type | Mandatory | Description |
| ---- | --------------------- | ---- | -------------- |
| taskInfo | [TaskInfo](#taskinfo) | Yes | Specific information about the specified background loading task, including the task ID and target AbilityName. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [workScheduler Error Codes](errorcode-workScheduler.md).

| ID  | Error Message             |
| ---- | --------------------- |
| 201 | No permission. |
| 9700003 | System service operation failed. |
| 9700004 | Check on taskInfo failed. |

**Example**

```ts
  import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';
  import { backgroundLoader } from '@kit.BackgroundTasksKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  export default class TestAppMainUIAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        try {

            // Define the parameters of the background loading task.
            let taskInfo: backgroundLoader.TaskInfo = {
                taskId: 1,
                abilityName: 'TestAppMainUIAbility'
            }
            // Unregister the background loading task. The system deletes the registration record.
            backgroundLoader.unregisterTask(taskInfo);
            console.info('unregisterTask success');
        } catch (error) {
            console.error(`backgroundLoader.unregisterTask catch error, code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
    }
  }
```

## backgroundLoader.getTaskInfo

getTaskInfo(taskId: number): Promise\<TaskInfo>

Queries a registered background loading task. This API uses a promise to return the result.

**Since:** 26.1.0

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | -------- |
| taskId | number | Yes | ID of the background loading task to query. The value is an integer. |

**Return value** 

| Type | Description |
| ------------------------------- | ---------------------------------------- |
| Promise\<[TaskInfo](#taskinfo)> | Promise used to return the result. If the passed task ID is a registered task ID, the task obtained from **WorkSchedulerService** is returned; otherwise, an exception is thrown. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [workScheduler Error Codes](errorcode-workScheduler.md).

| ID  | Error Message             |
| ---- | --------------------- |
| 201 | No permission. |
| 9700003 | System service operation failed. |
| 9700004 | Check on taskId failed. |

**Example**

```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { backgroundLoader } from '@kit.BackgroundTasksKit';
  
  let taskId: number = 1;
  backgroundLoader.getTaskInfo(taskId).then((taskInfo: backgroundLoader.TaskInfo) => {
    console.info(`workschedulerLog getTaskInfo success, ${JSON.stringify(taskInfo)}`);
  }).catch((error: BusinessError) => {
    console.error(`workschedulerLog getTaskInfo failed. code is ${error.code} message is ${error.message}`);
  })
``` 

## backgroundLoader.finishTask

finishTask(taskInfo: TaskInfo): void
 
After background loading is complete, the app must call **finishTask** in an independent thread of the asynchronous callback to notify the system of the task completion state.

**Since:** 26.1.0

**Timeout interval:** The app must ensure that the background loading task is completed within 30 seconds. If the cumulative number of timeouts reaches the system threshold when the app executes background loading tasks, the system disables subsequent background loading task scheduling.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**Model restriction**: This API can be used only in the stage model.

**Parameters**
| Name | Type | Mandatory | Description |
| ---- | --------------------- | ---- | -------------- |
| taskInfo | [TaskInfo](#taskinfo) | Yes | Specific information of the background loading task, including the task ID and the target AbilityName. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [workScheduler Error Codes](errorcode-workScheduler.md).

| ID  | Error Message             |
| ---- | --------------------- |
| 201 | No permission. |
| 9700003 | System service operation failed. |
| 9700004 | Check on taskInfo failed. |

**Example**

```ts
  import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';
  import { backgroundLoader } from '@kit.BackgroundTasksKit';
  import { rpc } from '@kit.IPCKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  // Define the ReplyParcelable return type as needed.
  class ReplyParcelable implements rpc.Parcelable {
    marshalling(dataOut: rpc.MessageSequence): boolean {
        return true;
    }
    unmarshalling(dataIn: rpc.MessageSequence): boolean {
        return true;
    }
  }
  // 01. Define the onStart callback method for background loading.
  function BackgroundLoaderOnStart(parcelData: rpc.MessageSequence): rpc.Parcelable {
    console.info(`background loader Task OnStart`);
    // TODO: Execute the business logic of app background loading.
    try {
        // Notify the system that the prefetch task is complete, so that the app can be frozen in advance.
        let taskInfo:  backgroundLoader.TaskInfo = {
            taskId: parcelData.readInt(),
            abilityName: parcelData.readString()
        };
        backgroundLoader.finishTask(taskInfo);
    } catch (error) {
        console.error(`backgroundLoader.finishTask catch error, code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
    return new ReplyParcelable();
  }

  // 02. Define the onStop callback method for background loading.
  function BackgroundLoaderOnStop(parcelData: rpc.MessageSequence): rpc.Parcelable {
    let taskId: number = parcelData.readInt();
    let abilityName: string = parcelData.readString();
    let stopCode: number = parcelData.readInt();
    let stopMessage: string = parcelData.readString();

    console.info(`background loader Task OnStop, taskId ${taskId}`);
    return new ReplyParcelable();
  }

  export default class TestAppMainUIAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        console.info('Callee onCreate is called');
        try {
            // 03. Declare the callback method for background loading. Use the callback method name defined for background loading as the parameter name.
            this.callee.on(backgroundLoader.ON_START, BackgroundLoaderOnStart);
            this.callee.on(backgroundLoader.ON_STOP, BackgroundLoaderOnStop);

            let taskInfo: backgroundLoader.TaskInfo = {
                taskId: 1,
                abilityName: 'TestAppMainUIAbility'
            }

            // 04. Register and start the background loading task. The system persists the task record for subsequent scheduling.
            backgroundLoader.registerTask(taskInfo);
            console.info('registerTask success');
        } catch (error) {
            console.error(`backgroundLoader.registerTask catch error, code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
    }
}
```

## TaskInfo

Defines the background loading task information specified by the app.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

| Name             | Type                                | Read-Only   | Optional   | Description               |
| --------------- | --------------------------------- | ---- | ---- | ---------------- |
| taskId          | number                            | No    | No    | Task ID specified by the app. The value type is an integer.          |
| abilityName     | string                            | No    | No    | Name of the main UIAbility for background loading that the app requires. Currently, each app supports only its own main UIAbility. |


## TaskStopInfo

When the system calls the **ON_STOP** API of the app, if the app needs to handle the specific reason for stopping the task, it must deserialize the parameter to obtain the **TaskStopInfo** struct. For a complete example, see the [finishTask](#backgroundloaderfinishtask) function.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

| Name             | Type                              | Read-Only | Optional | Description               |
| --------------- | --------------------------------- | ---- | ---- | ---------------- |
| taskId          | number                            | No    | No    | Task ID specified by the app. The value type is an integer.          |
| abilityName     | string                            | No    | No    | Name of the main UIAbility for background loading specified by the app. Currently, each app supports only its own main UIAbility. |
| stopCode        | [StopCode](#stopcode)                            | No    | No    | Error code for task stop.          |
| stopMessage     | string                            | No    | No    | Description of the error code for stopping the task. |

## StopCode

Enumerates the error codes in the **TaskStopInfo** parameter struct when the system calls the **onStop** API of the app.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

| Name                     | Value  | Description                      |
| ---------------------- | ---- | ----------------------- |
| SUCCESS       | 0    | The task is executed successfully.     |
| SYSTEM_ERROR    | 1    | A system error occurs during task execution.    |
| PERCEPTIBLE_ERROR  | 2    | A perceptible task error occurs during task execution.   |
| TIMEOUT_ERROR | 3    | The task execution times out. |
| EXECUTE_ERROR  | 4    | An exception occurs during task execution.  |

