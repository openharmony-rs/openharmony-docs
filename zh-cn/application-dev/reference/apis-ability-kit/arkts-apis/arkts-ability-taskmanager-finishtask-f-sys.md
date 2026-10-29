# finishTask（系统接口）

## 导入模块

```TypeScript
import { taskManager } from '@kit.AbilityKit';
```

## finishTask

```TypeScript
function finishTask(taskId: string): Promise<void>
```

以指定任务 ID 结束任务。撤销对归因到该任务的进程施加的资源管控，恢复进程的调度状态。任务不存在或已结束时，该 promise 被拒绝。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-taskManager-function finishTask(taskId: string): Promise<void>--><!--Device-taskManager-function finishTask(taskId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskId | string | 是 | 任务 ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System App. Interface caller is not a system app. |
| [16000302](../errorcode-ability.md#16000302-任务不存在) | Task not found. |
