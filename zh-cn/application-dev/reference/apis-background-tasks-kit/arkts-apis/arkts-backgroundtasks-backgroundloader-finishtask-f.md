# finishTask

## 导入模块

```TypeScript
import { backgroundLoader } from '@kit.BackgroundTasksKit';
```

## finishTask

```TypeScript
function finishTask(taskInfo: TaskInfo): void
```

结束后台加载任务。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskInfo | TaskInfo | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | 后台加载任务信息。 |
| [9700003](../errorcode-workScheduler.md#9700003-系统服务失败) | System service operation failed. |
| [9700004](../errorcode-workScheduler.md#9700004-参数校验失败) | Check on taskInfo failed. |
