# @ohos.app.agent.taskManager

The **taskManager** module provides APIs for managing the lifecycle of tasks. A task is the attribution unit for the execution of user intents: during the lifetime of a task, the processes attributed to the task are managed by the system according to the task priority.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace taskManager--><!--Device-unnamed-declare namespace taskManager-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## Modules to Import

```TypeScript
import { taskManager } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [finishTask](arkts-ability-taskmanager-finishtask-f-sys.md#finishtask-1) | Ends the task with the specified task ID. The resource management applied to the processes attributed to the task is revoked, and the scheduling state of the processes is restored. If the task does not exist or has already ended, this promise is rejected. |
| [startTask](arkts-ability-taskmanager-starttask-f-sys.md#starttask-1) | Starts a task with the specified task ID. The task is activated immediately, and the processes attributed to the task are managed by the system according to the specified priority. The task remains active until finishTask is called or the task is automatically ended by the system (for example, when the task times out or the creator process exits). If a task with the specified task ID already exists, this promise is rejected. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [TaskPriority](arkts-ability-taskmanager-taskpriority-e.md) | Enumerates the task priorities. |
