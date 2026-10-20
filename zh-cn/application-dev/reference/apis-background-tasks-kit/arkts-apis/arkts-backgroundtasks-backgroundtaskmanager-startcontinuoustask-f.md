# startContinuousTask

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## startContinuousTask

```TypeScript
function startContinuousTask(context: Context, request: ContinuousTaskRequest): Promise<number>
```

申请长时任务，一个UIAbility（FA模型则为ServiceAbility）下支持通过本接口申请多个长时任务，使用Promise异步回调。

通过本接口申请长时任务时，支持与已存在的长时任务合并通知，具体请参考[ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md)。

同一时间最多可存在10个长时任务，长时任务申请成功后，会有通知栏消息，没有提示音。

如果通过本接口申请的一个长时任务中同时包含多种类型，且包含数据传输类型，则在通知栏会发送2个长时任务通知，一个为数据传输类型，另一个为其他类型的合并通知。任意一个通知被移除时，长时任务取消，且另一个通知也会同步移除。

通过本接口申请长时任务时，支持包含数据传输类型的长时任务直接发送进度模版通知，可选择通知是否有进度环，进度为100时是否响铃，具体请参考[ProgressInfo](arkts-backgroundtasks-backgroundtaskmanager-progressinfo-i.md)。也可以通过[updateDataTransferProgress()](arkts-backgroundtasks-backgroundtaskmanager-updatedatatransferprogress-f.md)接口更新长时任务通知

**起始版本：** 26.0.1

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-backgroundTaskManager-function startContinuousTask(context: Context, request: ContinuousTaskRequest): Promise<int>--><!--Device-backgroundTaskManager-function startContinuousTask(context: Context, request: ContinuousTaskRequest): Promise<int>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用运行的上下文。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。<br> **说明：** Stage模型中，仅支持UIAbility申请。 |
| request | [ContinuousTaskRequest](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskrequest-c.md) | 是 | 长时任务请求信息，包括长时任务主类型、子类型等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回长时任务ID |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9800001](../errorcode-backgroundTaskMgr.md#9800001-内存操作失败) | Memory operation failed. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9800005](../errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |
| [9800006](../errorcode-backgroundTaskMgr.md#9800006-长时任务通知信息校验失败) | Notification verification failed for a continuous task. |
| [9800007](../errorcode-backgroundTaskMgr.md#9800007-长时任务信息存储失败) | Continuous task storage failed. |
| [9800008](../errorcode-backgroundTaskMgr.md#9800008-请求的长时任务不支持此设备类型) | The requested continuous task is not supported on this device type. |
