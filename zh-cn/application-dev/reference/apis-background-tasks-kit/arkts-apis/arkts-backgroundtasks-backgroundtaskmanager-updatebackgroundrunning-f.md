# updateBackgroundRunning

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

<a id="updatebackgroundrunning"></a>
## updateBackgroundRunning

```TypeScript
function updateBackgroundRunning(context: Context, bgModes: string[]): Promise<ContinuousTaskNotification>
```

更新长时任务类型，使用Promise异步回调。长时任务更新成功后，会有通知栏消息，没有提示音。</br>更新长时任务前，可以通过[getAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-getallcontinuoustasks-f.md#getallcontinuoustasks-1)接口获取当前所有长时任务信息，如果当前没有已经存在的长时任务，会更新失败。</br>该接口仅支持更新如下三个接口申请的长时任务：</br>[startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback:AsyncCallback&lt;void&gt;): void](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-1)</br>[startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise&lt;void&gt;](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-1)</br>[startBackgroundRunning(context: Context, bgModes: string[], wantAgent: WantAgent):Promise&lt;ContinuousTaskNotification&gt;]{@link backgroundTaskManager.startBackgroundRunning(context: Context,bgModes: string[], wantAgent: WantAgent)}

**起始版本：** 12

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-backgroundTaskManager-function updateBackgroundRunning(context: Context, bgModes: string[]): Promise<ContinuousTaskNotification>--><!--Device-backgroundTaskManager-function updateBackgroundRunning(context: Context, bgModes: string[]): Promise<ContinuousTaskNotification>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用运行的上下文。<br><br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 <br> **说明：** Stage模型中，仅支持UIAbility申请；FA模型中，仅支持ServiceAbility申请。 |
| bgModes | string[] | 是 | 更新后的长时任务类型<br>取值范围请参考长时任务类型中的[配置项](docroot://task-management/continuous-task.md#使用场景)。<br> **说明：** 支持传入一个或多个类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ContinuousTaskNotification&gt; | Promise对象，返回[ContinuousTaskNotification](arkts-backgroundtasks-backgroundtaskmanager-continuoustasknotification-i.md)类型对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameters types; 3. Parameter verification failed. |
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
      // 必须先执行startBackgroundRunning，才能调用updateBackgroundRunning，这里假设已经申请过
      let list: Array<string> = ['audioPlayback'];
      backgroundTaskManager.updateBackgroundRunning(this.context, list).then(() => {
        console.info('Operation updateBackgroundRunning succeeded');
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

更新长时任务，使用Promise异步回调。长时任务更新成功后，会有通知栏消息，没有提示音。

更新长时任务还存在如下约束限制：

1. 本接口仅支持更新如下接口申请的长时任务：[startBackgroundRunning(context: Context, request: ContinuousTaskRequest):Promise&lt;ContinuousTaskNotification&gt;](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-1)。2. 已经合并的长时任务，且后台任务主类型和子类型均相同，仅支持更新ContinuousTaskRequest.wantAgent中的wants信息（abilityName等），如果类型不同，更新失败。3. 如果待更新的长时任务或指定的更新类型中包含数据传输类型，直接返回失败。

**起始版本：** 21

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-backgroundTaskManager-function updateBackgroundRunning(context: Context, request: ContinuousTaskRequest): Promise<ContinuousTaskNotification>--><!--Device-backgroundTaskManager-function updateBackgroundRunning(context: Context, request: ContinuousTaskRequest): Promise<ContinuousTaskNotification>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用运行的上下文<br><br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 <br> **说明：** Stage模型中，仅支持UIAbility申请；FA模型中，仅支持ServiceAbility申请。 |
| request | [ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md) | 是 | 长时任务请求信息，包括待更新的长时任务ID等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ContinuousTaskNotification&gt; | Promise对象，返回更新后的长时任务通知信息，包括长时任务ID等。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [9800001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800001-内存操作失败) | Memory operation failed. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |
| [9800006](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800006-长时任务通知信息校验失败) | Notification verification failed for a continuous task. |
| [9800007](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800007-长时任务信息存储失败) | Continuous task storage failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { wantAgent, WantAgent } from '@kit.AbilityKit';
// 在原子化服务中，请删除WantAgent导入

export default class EntryAbility extends UIAbility {
  notificationId: number = 0; // 保存通知id
  continuousTaskId: number | undefined = -1; // 长时任务ID
  onCreate() {
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      // 添加需要被拉起应用的bundleName和abilityName, 请开发者替换为实际的bundleName和abilityName
      wants: [
        {
          bundleName: 'com.example.myapplication',
          abilityName: 'EntryAbility'
        }
      ],
      // 设置点击通知后的动作类型
      actionType: wantAgent.OperationType.START_ABILITY,
      // 开发者自定义的请求码，用于标识将被执行的动作
      requestCode: 0,
      // 设置点击通知后的动作执行属性
      wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
    };

    try {
      // 通过wantAgent模块下getWantAgent方法获取WantAgent对象
      // 在原子化服务中，请使用wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: object) => {替换下面一行代码
      wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: WantAgent) => {
        try {
          // 必须先执行startBackgroundRunning，才能调用updateBackgroundRunning，请开发者提前申请长时任务
          let modeList: Array<number> = [backgroundTaskManager.BackgroundTaskMode.MODE_LOCATION];
          let subModeList: Array<number> = [backgroundTaskManager.BackgroundTaskSubmode.SUBMODE_NORMAL_NOTIFICATION];
          let continuousTaskRequest = new backgroundTaskManager.ContinuousTaskRequest();
          continuousTaskRequest.backgroundTaskModes = modeList;
          continuousTaskRequest.backgroundTaskSubmodes = subModeList;
          continuousTaskRequest.wantAgent = wantAgentObj;
          continuousTaskRequest.combinedTaskNotification = false;
          continuousTaskRequest.continuousTaskId = this.continuousTaskId; // 对于更新接口，长时任务ID必须要传且为存在的ID，否则更新失败
          backgroundTaskManager.updateBackgroundRunning(this.context, continuousTaskRequest).then((res: backgroundTaskManager.ContinuousTaskNotification) => {
            console.info('Operation updateBackgroundRunning succeeded');
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

