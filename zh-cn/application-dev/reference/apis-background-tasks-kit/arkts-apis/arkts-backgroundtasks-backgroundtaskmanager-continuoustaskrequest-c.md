# ContinuousTaskRequest

通常作为[startBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-1)和[updateBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md#updatebackgroundrunning-1)接口的入参，用于指定申请或更新的长时任务信息。其中：

1. 通过[startBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-1)接口申请长时任务时，如果待申请长时任务与当前应用下已存在长时任务，两者的主类型和子类型均相同，且combinedTaskNotification均取值为true，则会合并通知。否则不会合并通知。2. 如果长时任务本身没有通知，则不会合并，长时任务类型是否会通知请参考[BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md)。3. 如果长时任务类型中包含数据传输类型，则不会合并通知。4. 通知合并后不能取消合并，已合并的不能更新成不合并。5. 通知合并后，点击通知栏消息，会跳转到第一个申请的长时任务对应的UIAbility，如果调用了更新接口，则跳转到最后一次更新的长时任务对应的UIAbility。6. 通过[updateBackgroundRunning()](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md#updatebackgroundrunning-1)接口更新长时任务时，传入的continuousTaskId必须存在，否则更新失败。7. 从API version 22开始支持特殊场景类型[MODE_SPECIAL_SCENARIO_PROCESSING](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md)的长时任务。必须单独使用且不支持通知合并，即申请或更新长时任务时，长时任务类型只能有特殊场景类型，否则返回错误。

**起始版本：** 21

<!--Device-backgroundTaskManager-export class ContinuousTaskRequest--><!--Device-backgroundTaskManager-export class ContinuousTaskRequest-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

<a id="checkspecialscenarioauth"></a>
## checkSpecialScenarioAuth

```TypeScript
checkSpecialScenarioAuth(context: Context): Promise<UserAuthResult>
```

查询用户是否授权能在后台长时间运行。使用Promise异步回调。

**起始版本：** 22

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinuousTaskRequest-checkSpecialScenarioAuth(context: Context): Promise<UserAuthResult>--><!--Device-ContinuousTaskRequest-checkSpecialScenarioAuth(context: Context): Promise<UserAuthResult>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用运行的上下文<br><br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 <br> **说明：** Stage模型中，仅支持UIAbility申请；FA模型中，仅支持ServiceAbility申请。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;UserAuthResult&gt; | Promise对象，返回用户授权结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
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

<a id="checkspecialscenarioauthresult"></a>
## checkSpecialScenarioAuthResult

```TypeScript
checkSpecialScenarioAuthResult(context: Context): Promise<UserAuthResult>
```

特殊场景长时任务申请用户授权，未授权时不会抛出异常。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinuousTaskRequest-checkSpecialScenarioAuthResult(context: Context): Promise<UserAuthResult>--><!--Device-ContinuousTaskRequest-checkSpecialScenarioAuthResult(context: Context): Promise<UserAuthResult>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;UserAuthResult&gt; | 用户授权结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | 无权限 |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | 系统服务无响应 |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | 长时任务校验错误 |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
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

<a id="ismodesupported"></a>
## isModeSupported

```TypeScript
isModeSupported(): boolean
```

查询当前[ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md)设置的长时任务主类型，是否支持申请长时任务。是否支持申请长时任务请参考[BackgroundTaskMode](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md)的说明。

**起始版本：** 21

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContinuousTaskRequest-isModeSupported(): boolean--><!--Device-ContinuousTaskRequest-isModeSupported(): boolean-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回长时任务主类型是否支持。true表示支持，false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
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

<a id="requestauthfromuser"></a>
## requestAuthFromUser

```TypeScript
requestAuthFromUser(context: Context, callback: Callback<UserAuthResult>): void
```

请求用户授权是否能在后台长时间运行，使用callback异步回调。接口调用成功会弹出用户授权弹框，建议应用在前台时调用该接口，提示用户进行授权。仅适用于特殊场景类型[MODE_SPECIAL_SCENARIO_PROCESSING](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskmode-e.md)的长时任务。

**起始版本：** 22

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinuousTaskRequest-requestAuthFromUser(context: Context, callback: Callback<UserAuthResult>): void--><!--Device-ContinuousTaskRequest-requestAuthFromUser(context: Context, callback: Callback<UserAuthResult>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用运行的上下文。<br><br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 <br> **说明：** Stage模型中，仅支持UIAbility申请；FA模型中，仅支持ServiceAbility申请。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;UserAuthResult&gt; | 是 | 用户操作后，返回授权结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const callbackAuth = (authResult: backgroundTaskManager.UserAuthResult) => {
  console.info('Operation requestAuthFromUser success. auth result: ' + JSON.stringify(authResult));
}

export default class EntryAbility extends UIAbility {
  onCreate() {
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

<a id="requestauthfromuserbydialog"></a>
## requestAuthFromUserByDialog

```TypeScript
requestAuthFromUserByDialog(context: Context, callback: Callback<UserAuthResult>): void
```

向用户请求MODE_SPECIAL_SCENARIO_PROCESSING授权时，会弹出对话框。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinuousTaskRequest-requestAuthFromUserByDialog(context: Context, callback: Callback<UserAuthResult>): void--><!--Device-ContinuousTaskRequest-requestAuthFromUserByDialog(context: Context, callback: Callback<UserAuthResult>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | App running context. |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;UserAuthResult&gt; | 是 | The callback of the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

const callbackAuth = (authResult: backgroundTaskManager.UserAuthResult) => {
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
set backgroundTaskModes(value: BackgroundTaskMode[])
```

长时任务主类型

**说明：** 主类型与子类型必须匹配。

**类型：** BackgroundTaskMode[]

**起始版本：** 21

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContinuousTaskRequest-set backgroundTaskModes(value: BackgroundTaskMode[])--><!--Device-ContinuousTaskRequest-set backgroundTaskModes(value: BackgroundTaskMode[])-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## backgroundTaskSubmodes

```TypeScript
set backgroundTaskSubmodes(value: BackgroundTaskSubmode[])
```

长时任务子类型。

**说明：** 主类型与子类型必须匹配。

**类型：** BackgroundTaskSubmode[]

**起始版本：** 21

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContinuousTaskRequest-set backgroundTaskSubmodes(value: BackgroundTaskSubmode[])--><!--Device-ContinuousTaskRequest-set backgroundTaskSubmodes(value: BackgroundTaskSubmode[])-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## combinedTaskNotification

```TypeScript
combinedTaskNotification?: boolean
```

是否合并通知，true表示合并，false表示不合并，默认为false。

**说明：** 该属性在[updateBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md#updatebackgroundrunning-1)接口中不生效，如需在已有任务上合并通知，请重新申请该任务，并在申请时设置为支持合并。

**类型：** boolean

**起始版本：** 21

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContinuousTaskRequest-combinedTaskNotification?: boolean--><!--Device-ContinuousTaskRequest-combinedTaskNotification?: boolean-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## continuousTaskId

```TypeScript
continuousTaskId?: number
```

长时任务ID，默认值为-1。

**说明：** 如果combinedTaskNotification取值为true，则该值为必填项，且必须是存在的ID。

作为[updateBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-updatebackgroundrunning-f.md#updatebackgroundrunning-1)接口入参时，该属性必填，且必须是存在的ID。

可以通过[getAllContinuousTasks](arkts-backgroundtasks-backgroundtaskmanager-getallcontinuoustasks-f.md#getallcontinuoustasks-1)接口查看当前所有长时任务信息。

**类型：** number

**起始版本：** 21

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContinuousTaskRequest-continuousTaskId?: number--><!--Device-ContinuousTaskRequest-continuousTaskId?: number-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## wantAgent

```TypeScript
set wantAgent(value: WantAgent)
```

通知参数，用于指定点击长时任务通知后跳转的界面。

**类型：** WantAgent

**起始版本：** 21

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContinuousTaskRequest-set wantAgent(value: WantAgent)--><!--Device-ContinuousTaskRequest-set wantAgent(value: WantAgent)-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

