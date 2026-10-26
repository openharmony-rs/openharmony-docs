# startTask (System API)

## Modules to Import

```TypeScript
import { taskManager } from '@kit.AbilityKit';
```

## startTask

```TypeScript
function startTask(taskId: string, priority?: TaskPriority): Promise<void>
```

Starts a task with the specified task ID. The task is activated immediately, and the processes attributed to the task are managed by the system according to the specified priority. The task remains active until finishTask is called or the task is automatically ended by the system (for example, when the task times out or the creator process exits). If a task with the specified task ID already exists, this promise is rejected.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-taskManager-function startTask(taskId: string, priority?: TaskPriority): Promise<void>--><!--Device-taskManager-function startTask(taskId: string, priority?: TaskPriority): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | Yes | ID of the task, which is used as the attribution key for the processes launched during the task execution. The value must contain 1 to 256 characters. |
| priority | [TaskPriority](arkts-ability-taskmanager-taskpriority-e.md) | No | Priority of the task. The default value is **MEDIUM**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| 16000301 | Task already exists. |
