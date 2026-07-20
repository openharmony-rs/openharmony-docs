# startBackgroundRunning

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

<a id="startbackgroundrunning"></a>
## startBackgroundRunning

```TypeScript
function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback<void>): void
```

申请长时任务，支持申请一种类型，使用callback异步回调。长时任务申请成功后，会有通知栏消息，没有提示音。一个UIAbility（FA模型则为ServiceAbility）同一时刻仅支持通过本接口支持申请一个长时任务，可以通过API version 21新增接口[startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-1)申请多个长时任务。

**起始版本：** 9

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-backgroundTaskManager-function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback<void>): void--><!--Device-backgroundTaskManager-function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用运行的上下文。<br><br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 <br> **说明：** Stage模型中，仅支持UIAbility申请；FA模型中，仅支持ServiceAbility申请。 |
| bgMode | [BackgroundMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundmode-e.md) | 是 | 长时任务类型。 |
| wantAgent | [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md) | 是 | 通知参数，用于指定点击长时任务通知后跳转的界面。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，申请长时任务成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
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
import { wantAgent, WantAgent } from '@kit.AbilityKit';
// 在原子化服务中，请删除WantAgent导入

const callback = (error: BusinessError, data: void) => {
  if (error) {
    console.error(`Operation startBackgroundRunning failed. code is ${error.code} message is ${error.message}`);
  } else {
    console.info('Operation startBackgroundRunning succeeded');
  }
}

export default class EntryAbility extends UIAbility {
  onCreate() {
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      // 点击通知后，将要执行的动作列表
      wants: [
        {
          bundleName: 'com.example.myapplication',
          abilityName: 'EntryAbility'
        }
      ],
      // 点击通知后，动作类型
      actionType: wantAgent.OperationType.START_ABILITY,
      // 使用者自定义的一个私有值
      requestCode: 0,
      // 点击通知后，动作执行属性
      wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
    };

    try {
      // 通过wantAgent模块下getWantAgent方法获取WantAgent对象
      // 在原子化服务中，请使用wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: object) => {替换下面一行代码
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


<a id="startbackgroundrunning-1"></a>
## startBackgroundRunning

```TypeScript
function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise<void>
```

申请长时任务，支持申请一种类型，使用Promise异步回调。长时任务申请成功后，会有通知栏消息，没有提示音。一个UIAbility（FA模型则为ServiceAbility）同一时刻仅支持通过本接口支持申请一个长时任务，可以通过API version 21新增接口[startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-1)申请多个长时任务。

**起始版本：** 9

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-backgroundTaskManager-function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise<void>--><!--Device-backgroundTaskManager-function startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise<void>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用运行的上下文。<br><br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 <br> **说明：** Stage模型中，仅支持UIAbility申请；FA模型中，仅支持ServiceAbility申请。 |
| bgMode | [BackgroundMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundmode-e.md) | 是 | 长时任务类型。 |
| wantAgent | [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md) | 是 | 通知参数，用于指定点击长时任务通知后跳转的界面。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
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
import { wantAgent, WantAgent } from '@kit.AbilityKit';
// 在原子化服务中，请删除WantAgent导入

export default class EntryAbility extends UIAbility {
  onCreate() {
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      // 点击通知后，将要执行的动作列表
      wants: [
        {
          bundleName: 'com.example.myapplication',
          abilityName: 'EntryAbility'
        }
      ],
      // 点击通知后，动作类型
      actionType: wantAgent.OperationType.START_ABILITY,
      // 使用者自定义的一个私有值
      requestCode: 0,
      // 点击通知后，动作执行属性
      wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
    };

    try {
      // 通过wantAgent模块下getWantAgent方法获取WantAgent对象
      // 在原子化服务中，请使用wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: object) => {替换下面一行代码
      wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: WantAgent) => {
        try {
          backgroundTaskManager.startBackgroundRunning(this.context,
            backgroundTaskManager.BackgroundMode.AUDIO_PLAYBACK, wantAgentObj).then(() => {
              console.info('Operation startBackgroundRunning succeeded');
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


<a id="startbackgroundrunning-2"></a>
## startBackgroundRunning

```TypeScript
function startBackgroundRunning(context: Context, bgModes: string[], wantAgent: WantAgent): Promise<ContinuousTaskNotification>
```

申请长时任务，支持申请多种类型，使用Promise异步回调。长时任务申请成功后，会有通知栏消息，没有提示音。一个UIAbility（FA模型则为ServiceAbility）同一时刻仅支持通过本接口支持申请一个长时任务，可以通过API version 21新增接口[startBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-1)申请多个长时任务。

**起始版本：** 12

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-backgroundTaskManager-function startBackgroundRunning(context: Context, bgModes: string[], wantAgent: WantAgent): Promise<ContinuousTaskNotification>--><!--Device-backgroundTaskManager-function startBackgroundRunning(context: Context, bgModes: string[], wantAgent: WantAgent): Promise<ContinuousTaskNotification>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用运行的上下文<br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 <br> **说明：** Stage模型中，仅支持UIAbility申请；FA模型中，仅支持ServiceAbility申请。 |
| bgModes | string[] | 是 | 长时任务类型<br>取值范围请参考长时任务类型中的[配置项](docroot://task-management/continuous-task.md#使用场景)。<br>**说明：** 支持传入一个或多个类型。 |
| wantAgent | [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md) | 是 | 通知参数，用于指定点击长时任务通知后跳转的界面。 |

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
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationManager } from '@kit.NotificationKit';
import { wantAgent, WantAgent } from '@kit.AbilityKit';
// 在原子化服务中，请删除WantAgent导入

export default class EntryAbility extends UIAbility {
  notificationId: number = 0; // 保存通知Id

  onCreate() {
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      // 点击通知后，将要执行的动作列表
      wants: [
        {
          bundleName: 'com.example.myapplication',
          abilityName: 'EntryAbility'
        }
      ],
      // 点击通知后，动作类型
      actionType: wantAgent.OperationType.START_ABILITY,
      // 使用者自定义的一个私有值
      requestCode: 0,
      // 点击通知后，动作执行属性
      wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
    };

    try {
      // 通过wantAgent模块下getWantAgent方法获取WantAgent对象
      // 在原子化服务中，请使用wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: object) => {替换下面一行代码
      wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: WantAgent) => {
        try {
          // 当长时任务类型包含数据传输(dataTransfer)时，应用需要更新进度，其他类型不需要
          let list: Array<string> = ['dataTransfer'];
          // 在原子化服务中，let list: Array<string> = ['audioPlayback'];
          backgroundTaskManager.startBackgroundRunning(this.context, list, wantAgentObj).then((res: backgroundTaskManager.ContinuousTaskNotification) => {
            console.info('Operation startBackgroundRunning succeeded');
            // 对于上传下载类的长时任务，应用可以使用res中返回的notificationId来更新通知，比如发送带进度条的模板通知
            this.notificationId = res.notificationId;
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

  // 当长时任务类型包含数据传输(dataTransfer)时，应用需要更新进度，其他类型不需要
  updateProcess(process: number) {
    // 定义通知类型，更新进度时的通知类型必须为实况窗
    let downLoadTemplate: notificationManager.NotificationTemplate = {
      name: 'downloadTemplate', // 当前只支持downloadTemplate，保持不变
      data: {
        title: '文件下载：music.mp4', // 必填
        fileName: 'senTemplate', // 必填
        progressValue: process, // 应用更新进度值，自定义
      }
    };
    let request: notificationManager.NotificationRequest = {
      content: {
        // 系统实况类型，保持不变
        notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_SYSTEM_LIVE_VIEW,
        systemLiveView: {
          typeCode: 8, // 数据传输(dataTransfer)类型需要填写 8，当前仅支持此类型。保持不变
          title: 'test', // 应用自定义
          text: 'test', // 应用自定义
        }
      },
      id: this.notificationId, // 必须是申请长时任务返回的notificationId，否则应用更新通知失败
      notificationSlotType: notificationManager.SlotType.LIVE_VIEW, // 实况窗类型，保持不变
      template: downLoadTemplate // 应用需要设置的模版名称
    };

    try {
      notificationManager.publish(request).then(() => {
        console.info('publish success, id= ' + this.notificationId);
      }).catch((err: BusinessError) => {
        console.error(`publish fail: ${JSON.stringify(err)}`);
      });
    } catch (err) {
      console.error(`publish fail: ${JSON.stringify(err)}`);
    }
  }
};

```


<a id="startbackgroundrunning-3"></a>
## startBackgroundRunning

```TypeScript
function startBackgroundRunning(context: Context, request: ContinuousTaskRequest): Promise<ContinuousTaskNotification>
```

申请长时任务，一个UIAbility（FA模型则为ServiceAbility）下支持通过本接口申请多个长时任务，使用Promise异步回调。通过本接口申请长时任务时，支持与已存在的长时任务合并通知，具体请参考[ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md)。</br>同一时间最多可存在10个长时任务，长时任务申请成功后，会有通知栏消息，没有提示音。</br>如果通过本接口申请的一个长时任务中同时包含多种类型，且包含数据传输类型，则在通知栏会发送2个长时任务通知，一个为数据传输类型，另一个为其他类型的合并通知。任意一个通知被移除时，长时任务取消，且另一个通知也会同步移除。接口返回的长时任务通知Id为数据传输类型的Id，主要用于数据传输的进度更新。

**起始版本：** 21

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-backgroundTaskManager-function startBackgroundRunning(context: Context, request: ContinuousTaskRequest): Promise<ContinuousTaskNotification>--><!--Device-backgroundTaskManager-function startBackgroundRunning(context: Context, request: ContinuousTaskRequest): Promise<ContinuousTaskNotification>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用运行的上下文<br><br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 <br> **说明：** Stage模型中，仅支持UIAbility申请；FA模型中，仅支持ServiceAbility申请。 |
| request | [ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md) | 是 | 长时任务请求信息，包括长时任务主类型、子类型等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ContinuousTaskNotification&gt; | Promise对象，返回长时任务通知信息，包括长时任务ID等。 |

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
  continuousTaskId: number | undefined = -1;
  onCreate() {
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      // 请开发者替换为实际被拉起应用的bundleName和abilityName
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
          // 如果要合并通知，主类型和子类型都必须相同，combinedTaskNotification为true，continuousTaskId必须存在且合法
          // 申请主类型为MODE_LOCATION的长时任务
          let modeList: Array<number> = [backgroundTaskManager.BackgroundTaskMode.MODE_LOCATION];
          let subModeList: Array<number> = [backgroundTaskManager.BackgroundTaskSubmode.SUBMODE_NORMAL_NOTIFICATION];
          let continuousTaskRequest = new backgroundTaskManager.ContinuousTaskRequest();
          continuousTaskRequest.backgroundTaskModes =  modeList;
          continuousTaskRequest.backgroundTaskSubmodes = subModeList;
          continuousTaskRequest.wantAgent = wantAgentObj;
          continuousTaskRequest.combinedTaskNotification = false;
          continuousTaskRequest.continuousTaskId = this.continuousTaskId;
          backgroundTaskManager.startBackgroundRunning(this.context, continuousTaskRequest).then((res: backgroundTaskManager.ContinuousTaskNotification) => {
            console.info(`Operation startBackgroundRunning succeeded. notificationId is ${res.notificationId} continuousTaskId is ${res.continuousTaskId}`);
            this.notificationId = res.notificationId;
            this.continuousTaskId = res.continuousTaskId;
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

