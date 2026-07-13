# stopBackgroundRunning

## stopBackgroundRunning

```TypeScript
function stopBackgroundRunning(context: Context, callback: AsyncCallback<void>): void
```

取消当前UIAbility（FA模型则为ServiceAbility）下所有长时任务，使用callback异步回调。也可以通过
[stopBackgroundRunning](arkts-backgroundtasks-stopbackgroundrunning-f.md#stopbackgroundrunning-3)
接口取消指定Id的长时任务。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用运行的上下文。<br><br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 <br> **说明：** Stage模型中，仅支持UIAbility申请；FA模型中，仅支持ServiceAbility申请。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，取消长时任务成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 9 - 18 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [9800001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800001-内存操作失败) | Memory operation failed. |
| [9800002](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [9800003](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800003-ipc通信失败) | Internal transaction failed. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |
| [9800006](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800006-长时任务通知信息校验失败) | Notification verification failed for a continuous task. |
| [9800007](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800007-长时任务信息存储失败) | Continuous task storage failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';

const callback = (error: BusinessError, data: void) => {
  if (error) {
    console.error(`Operation stopBackgroundRunning failed. code is ${error.code} message is ${error.message}`);
  } else {
    console.info('Operation stopBackgroundRunning succeeded');
  }
}

export default class EntryAbility extends UIAbility {
  onCreate() {
    try {
      backgroundTaskManager.stopBackgroundRunning(this.context, callback);
    } catch (error) {
      console.error(`Operation stopBackgroundRunning failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};

```


## stopBackgroundRunning

```TypeScript
function stopBackgroundRunning(context: Context): Promise<void>
```

取消当前UIAbility（FA模型则为ServiceAbility）下所有长时任务，使用Promise异步回调。也可以通过
[stopBackgroundRunning](arkts-backgroundtasks-stopbackgroundrunning-f.md#stopbackgroundrunning-3)
接口取消指定Id的长时任务。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用运行的上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 9 - 18 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [9800001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800001-内存操作失败) | Memory operation failed. |
| [9800002](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [9800003](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800003-ipc通信失败) | Internal transaction failed. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |
| [9800006](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800006-长时任务通知信息校验失败) | Notification verification failed for a continuous task. |
| [9800007](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800007-长时任务信息存储失败) | Continuous task storage failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    try {
      backgroundTaskManager.stopBackgroundRunning(this.context).then(() => {
        console.info('Operation stopBackgroundRunning succeeded');
      }).catch((error: BusinessError) => {
        console.error(`Operation stopBackgroundRunning failed. code is ${error.code} message is ${error.message}`);
      });
    } catch (error) {
      console.error(`Operation stopBackgroundRunning failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};

```


## stopBackgroundRunning

```TypeScript
function stopBackgroundRunning(context: Context, continuousTaskId: number): Promise<void>
```

取消指定Id的长时任务，使用Promise异步回调。也可以通过
[stopBackgroundRunning](backgroundTaskManager.stopBackgroundRunning(context: Context, callback:AsyncCallback<void>))
取消当前UIAbility下所有长时任务。

**起始版本：** 21

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用运行的上下文。<br><br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 <br> **说明：** Stage模型中，仅支持UIAbility申请；FA模型中，仅支持ServiceAbility申请。 |
| continuousTaskId | number | 是 | 长时任务ID。<br>取值限定为整数。- 长时任务ID。<br>**说明：** 可以通过[startBackgroundRunning](backgroundTaskManager.startBackgroundRunning(context: Context, request:ContinuousTaskRequest))接口的返回值获取当前申请的长时任务ID，或者通过[getAllContinuousTasks](backgroundTaskManager.getAllContinuousTasks(context: Context, includeSuspended:boolean))接口获取所有长时任务信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9800001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800001-内存操作失败) | Memory operation failed. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |
| [9800006](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800006-长时任务通知信息校验失败) | Notification verification failed for a continuous task. |
| [9800007](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800007-长时任务信息存储失败) | Continuous task storage failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  continuousTaskId: number = 0;
  onCreate() {
    try {
      backgroundTaskManager.stopBackgroundRunning(this.context, this.continuousTaskId).then(() => {
        console.info('Operation stopBackgroundRunning succeeded');
      }).catch((error: BusinessError) => {
        console.error(`Operation stopBackgroundRunning failed. code is ${error.code} message is ${error.message}`);
      });
    } catch (error) {
      console.error(`Operation stopBackgroundRunning failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};

```

