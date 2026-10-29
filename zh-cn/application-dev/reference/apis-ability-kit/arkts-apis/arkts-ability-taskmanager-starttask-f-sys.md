# startTask（系统接口）

## 导入模块

```TypeScript
import { taskManager } from '@kit.AbilityKit';
```

## startTask

```TypeScript
function startTask(taskId: string, priority?: TaskPriority): Promise<void>
```

以指定任务 ID 启动任务。任务立即激活，系统按指定优先级对归因到该任务的进程进行管控。任务持续存活，直至调用 finishTask 或系统自动结束（如任务超时、创建者进程退出）。若指定任务 ID 的任务已存在，该 promise 被拒绝。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-taskManager-function startTask(taskId: string, priority?: TaskPriority): Promise<void>--><!--Device-taskManager-function startTask(taskId: string, priority?: TaskPriority): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskId | string | 是 | 任务 ID，作为任务执行期间所拉起进程的归因主键。长度范围为 1~256 个字符。 |
| priority | [TaskPriority](arkts-ability-taskmanager-taskpriority-e.md) | 否 | 任务优先级。默认值为**MEDIUM**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System App. Interface caller is not a system app. |
| [16000301](../errorcode-ability.md#16000301-任务已存在) | Task already exists. |
