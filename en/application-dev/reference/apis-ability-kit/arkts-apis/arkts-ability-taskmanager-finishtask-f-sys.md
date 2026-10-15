# finishTask (System API)

## Modules to Import

```TypeScript
import { taskManager } from '@kit.AbilityKit';
```

## finishTask

```TypeScript
function finishTask(taskId: string): Promise<void>
```

Ends the task with the specified task ID. The resource management applied to the processes attributed to the task is revoked, and the scheduling state of the processes is restored. If the task does not exist or has already ended, this promise is rejected.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-taskManager-function finishTask(taskId: string): Promise<void>--><!--Device-taskManager-function finishTask(taskId: string): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | Yes | ID of the task. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| 16000302 | Task not found. |
