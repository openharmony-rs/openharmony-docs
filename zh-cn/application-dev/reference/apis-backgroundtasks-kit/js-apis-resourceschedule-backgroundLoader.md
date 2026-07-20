# @ohos.resourceschedule.backgroundLoader (后台加载任务)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

本模块提供后台加载任务的注册、取消、查询的能力。在开发过程中，期望通过后台预先加载应用数据实现优化应用启动体验的开发者，可以调用本模块接口注册的后台加载任务，在系统空闲时根据内存、电量、壳温等情况进行调度执行。开发指导请参考[延迟任务开发指南](../../task-management/work-scheduler.md)。

>  **说明：**
>
>  本模块首批接口从API version 26开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>  本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { backgroundLoader } from '@kit.BackgroundTasksKit';
```

## backgroundLoader.registerTask

registerTask(taskInfo: TaskInfo): void

申请后台加载任务，成功后会把任务添加到后台加载任务队列，满足触发条件后由系统调度执行。

**需要权限**：ohos.permission.KEEP_BACKGROUND_RUNNING

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**参数**：
| 参数名  | 类型                    | 必填   | 说明             |
| ----   | --------------------- | ---- | -------------- |
| taskInfo | [TaskInfo](#taskinfo) | 是    | 指定后台加载任务具体信息，包括任务ID和目标AbilityName。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201 | No permission. |
| 9700003 | System service operation failed. |
| 9700004 | Check on taskInfo failed. |

**示例**：

```ts
  import { UIAbility, AbilityConstant } from '@kit.AbilityKit';
  import { backgroundLoader } from '@kit.BackgroundTasksKit';
  
  export default class TestAppMainUIAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        console.info('Callee onCreate is called');
        try {
            // 01.声明后台加载的回调方法，参数名使用后台加载定义好的回调方法
            this.callee.on(backgroundLoader.ON_START, BackgroundPrefetchOnStart);
            this.callee.on(backgroundLoader.ON_STOP, BackgroundPrefetchOnStop);

            // 02.定义后台加载任务的参数
            let taskInfo: backgroundLoader.TaskInfo = {
                taskId: 1,
                abilityName: 'TestAppMainUIAbility'
            }

            // 03.注册启动后台加载任务，系统将任务记录持久化保存，用于后续调度
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

取消注册后台加载任务。

**需要权限**：ohos.permission.KEEP_BACKGROUND_RUNNING

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**参数**：
| 参数名  | 类型                    | 必填   | 说明             |
| ----   | --------------------- | ---- | -------------- |
| taskInfo | [TaskInfo](#taskinfo) | 是    | 指定后台加载任务具体信息，包括任务ID和目标AbilityName。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201 | No permission. |
| 9700003 | System service operation failed. |
| 9700004 | Check on taskInfo failed. |

**示例**：

```ts
  import { UIAbility, AbilityConstant } from '@kit.AbilityKit';
  import { backgroundLoader } from '@kit.BackgroundTasksKit';
  
  export default class TestAppMainUIAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        console.info('Callee onCreate is called');
        try {
            // 01.声明后台加载的回调方法，参数名使用后台加载定义好的回调方法
            this.callee.on(backgroundLoader.ON_START, BackgroundPrefetchOnStart);
            this.callee.on(backgroundLoader.ON_STOP, BackgroundPrefetchOnStop);

            // 02.定义后台加载任务的参数
            let taskInfo: backgroundLoader.TaskInfo = {
                taskId: 1,
                abilityName: 'TestAppMainUIAbility'
            }

            // 03.注册启动后台加载任务，系统将任务记录持久化保存，用于后续调度
            backgroundLoader.unregisterTask(taskInfo);
            console.info('unregisterTask success');
        } catch (error) {
            console.error(`backgroundLoader.unregisterTask catch error, code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
    }
  }
```

## backgroundLoader.getTaskInfo

getTaskInfo(taskId: int): Promise\<TaskInfo>

查询以及注册的后台加载任务，使用Promise形式返回。

**需要权限**：ohos.permission.KEEP_BACKGROUND_RUNNING

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**参数**：

| 参数名    | 类型     | 必填   | 说明       |
| ------ | ------ | ---- | -------- |
| taskId | int   | 是    | 需要查询的后台加载任务ID |

**返回值**：

| 类型                              | 说明                                       |
| ------------------------------- | ---------------------------------------- |
| Promise\<[TaskInfo](#taskinfo)> | Promise对象，如果taskId有效，则返回从WorkSchedulerService获取的任务，否则抛出异常。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201 | No permission. |
| 9700003 | System service operation failed. |
| 9700004 | Check on taskId failed. |

**示例**：

```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { backgroundLoader } from '@kit.BackgroundTasksKit';
  
  let taskID: int = 1;
  backgroundLoader.getTaskInfo(taskId).then((taskInfo: backgroundLoader.TaskInfo) => {
    console.info(`workschedulerLog getTaskInfo success, ${JSON.stringify(res)}`);
  }).catch((error: BusinessError) => {
    console.error(`workschedulerLog getTaskInfo failed. code is ${error.code} message is ${error.message}`);
  })
``` 

## backgroundLoader.ON_START

const ON_START: string

应用需要实现后台加载任务onStart的回调方法， 在这个回调方法中实现后台处理应用页面数据的加载逻辑。应用需要将回调方法使用ON_START作为方法名通过Callee注册给系统。系统会通过Caller实现该回调。Callee/Caller回调机制的介绍请参考[Callee](../apis-ability-kit/js-apis-app-ability-uiAbility.md#callee)。 
代码示例参考finishTask函数的完整实例。

## backgroundLoader.ON_STOP

const ON_STOP: string

应用需要实现后台加载任务onStop的回调方法，处理后台加载任务被异常终止的情况。应用需要将回调方法使用ON_START作为方法名通过Callee注册给系统。系统会通过Caller实现该回调。Callee/Caller回调机制的介绍请参考[Callee](../apis-ability-kit/js-apis-app-ability-uiAbility.md#callee)。 
代码示例参考finishTask函数的完整实例。

## backgroundLoader.finishTask

finishTask(taskInfo: TaskInfo): void
 
应用需要实现后台加载任务的onStart的主业务回调方法，在完成业务加载任务后，需要通过调用finishTask方法通知系统加载任务完成。运行在异步回调函数或其他线程中执行finishTask调用。

**超时时间限制**：应用需要确保后台加载任务尽量在30秒内执行完成，从开始执行ON_START回调方法之后，需要在30秒内完成finishTask任务完成的调用。
如果应用在执行后台加载任务时出现多次超时，系统将禁用后续的后台加载任务调度。

**需要权限**：ohos.permission.KEEP_BACKGROUND_RUNNING

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**参数**：
| 参数名  | 类型                    | 必填   | 说明             |
| ----   | --------------------- | ---- | -------------- |
| taskInfo | [TaskInfo](#taskinfo) | 是    | 指定后台加载任务具体信息，包括任务ID和目标AbilityName。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201 | No permission. |
| 9700003 | System service operation failed. |
| 9700004 | Check on taskInfo failed. |

**示例**：

```ts
  import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';
  import { backgroundLoader } from '@kit.BackgroundTasksKit';
  import { rpc } from '@kit.IPCKit';
  
  // 01.定义后台加载的onStart回调方法
  function BackgroundLoaderOnStart(pdata: rpc.MessageSequence) {
    let taskInfo =  new backgroundLoader.TaskInfo();
    pdata.readParcelable(taskInfo);

    console.info(`background loader Task OnStart, taskInfo `${taskInfo.taskId});
    // TODO：执行应用后台加载的业务逻辑

    // 通知系统预取任务处理完成，可以提前冻结应用。
    backgroundLoader.finishTask(taskInfo);
  }

  // 02.定义后台加载的onStop回调方法
  function BackgroundPrefetchOnStop(pdata: rpc.MessageSequence) {
    let taskStopInfo = new backgroundLoader.TaskStopInfo();
    pdata.readParcelable(taskStopInfo);

    console.info(`background loader Task OnStop, taskInfo `${taskInfo.taskId});
  }

  export default class TestAppMainUIAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
        console.info('Callee onCreate is called');
        try {
            // 03.声明后台加载的回调方法，参数名使用后台加载定义好的回调方法
            this.callee.on(backgroundLoader.ON_START, BackgroundPrefetchOnStart);
            this.callee.on(backgroundLoader.ON_STOP, BackgroundPrefetchOnStop);

            let taskInfo: backgroundLoader.TaskInfo = {
                taskId: 1,
                abilityName: 'TestAppMainUIAbility'
            }

            // 04.注册启动后台加载任务，系统将任务记录持久化保存，用于后续调度
            backgroundLoader.unregisterTask(taskInfo);
            console.info('unregisterTask success');
        } catch (error) {
            console.error(`backgroundLoader.unregisterTask catch error, code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
    }
}
```

## TaskInfo

应用定义和指定的后台加载任务信息。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

| 名称             | 类型                                | 只读   | 可选   | 说明               |
| --------------- | --------------------------------- | ---- | ---- | ---------------- |
| taskId          | int                            | 否    | 否    |应用指定标识任务ID。          |
| abilityName     | string                            | 否    | 否    |应用需要实现后台加载主UIAbility名称，当前每个应用仅支持自身的主UIAbility。 |


## TaskStopInfo

系统回调应用的onStop方法中，若应用需要处理具体的任务停止原因，则需要从参数进行反序列化获得结构TaskStopInfo。具体参考finishTask函数中的完整示例代码。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

| 名称             | 类型                                | 只读   | 可选   | 说明               |
| --------------- | --------------------------------- | ---- | ---- | ---------------- |
| taskId          | int                            | 否    | 否    |应用指定标识任务ID。          |
| abilityName     | string                            | 否    | 否    |应用需要实现后台加载主UIAbility名称，当前每个应用仅支持自身的主UIAbility。 |
| stopCode        | [StopCode](#stopcode)                            | 否    | 否    |任务停止的错误码。          |
| stopMessage     | string                            | 否    | 否    |任务停止的错误码描述。 |

## StopCode

系统回调应用的onStop方法的TaskStopInfo参数结构体中的错误码枚举定义。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

| 名称                     | 值  | 说明                      |
| ---------------------- | ---- | ----------------------- |
| SUCCESS       | 0    | 表示执行成功。     |
| SYSTEM_ERROR    | 1    | 表示任务执行中发生系统错误。    |
| PERCEPTIBLE_ERROR  | 2    | 表示任务执行中发生可感知任务错误。   |
| TIMEOUT_ERROR | 3    | 表示任务执行超时。 |
| EXECUTE_ERROR  | 4    | 表示任务执行异常。  |
