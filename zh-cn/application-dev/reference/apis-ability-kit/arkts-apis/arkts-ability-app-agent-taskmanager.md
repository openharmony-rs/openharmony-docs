# @ohos.app.agent.taskManager

**taskManager**模块提供任务生命周期管理接口。任务是用户意图执行的归因单元：任务存活期间，系统按任务优先级对归因到该任务的进程进行管控。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace taskManager--><!--Device-unnamed-declare namespace taskManager-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## 导入模块

```TypeScript
import { taskManager } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [finishTask](arkts-ability-taskmanager-finishtask-f-sys.md#finishtask) | 以指定任务 ID 结束任务。撤销对归因到该任务的进程施加的资源管控，恢复进程的调度状态。任务不存在或已结束时，该 promise 被拒绝。 |
| [startTask](arkts-ability-taskmanager-starttask-f-sys.md#starttask) | 以指定任务 ID 启动任务。任务立即激活，系统按指定优先级对归因到该任务的进程进行管控。任务持续存活，直至调用 finishTask 或系统自动结束（如任务超时、创建者进程退出）。若指定任务 ID 的任务已存在，该 promise 被拒绝。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TaskPriority](arkts-ability-taskmanager-taskpriority-e.md) | 任务优先级枚举。 |
