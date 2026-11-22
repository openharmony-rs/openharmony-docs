# @ohos.app.agent.taskManager (Task Management) (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=c1aa700183d58930b5602a892918b785fdf7caf9 translatedAt=2026-11-14T08:07:09.003Z pushedAt=2026-11-14T08:14:05.565Z nl=1 -->

A task is an attribution unit for executing user intent. The taskManager module provides complete task lifecycle management capabilities, including starting and finishing tasks. While a task is alive, the system performs unified resource scheduling management on the processes attributed to the task based on the task priority.

A system application calls the startTask API to create and activate a task. A task can be finished in any of the following ways:
- The finishTask API is called to finish the task normally.
- The task times out and is automatically finished by the system.
- The process of the task creator exits, and the task is automatically finished by the system.

After a task is finished, the system revokes the resource management imposed on the processes attributed to the task, and the process scheduling state is restored accordingly. Task information is stored only in memory, and the task is automatically finished after the device restarts.

**Since:** 26.1.0

> **NOTE**
>
> The APIs of this module are all system APIs.

## Modules to Import

```ts
import { taskManager } from '@kit.AbilityKit';
```

## TaskPriority

Enumerates the task priorities. After a task is started, the system manages the processes attributed to the task based on the priority.

**Since:** 26.1.0

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model Constraint:** This API can be used only in the stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| LOW | 100 | Low priority. |
| MEDIUM | 200 | Medium priority. |
| HIGH | 300 | High priority. |

## taskManager.startTask

startTask(taskId: string, priority?: TaskPriority): Promise&lt;void&gt;

Starts the task with the specified task ID. The task is activated immediately. This API uses a promise to return the result asynchronously.

After the task is activated, the processes attributed to the task are managed by the system according to the specified priority. The task remains active until it is finished by calling [finishTask](#taskmanagerfinishtask) or is automatically finished by the system (for example, when the task times out or the creator process exits). If a task with the specified task ID already exists, error code 16000301 is returned.

> **NOTE**
>
> - The task timeout duration is configured by the system. The timeout timer starts when a managed process is last added to the task (or when the task is created if no managed process exists), and is refreshed each time a new managed process is added. When no new managed process is added within the system timeout duration (600s by default), the task is automatically finished by the system.
> - After the task creator process exits, the tasks created by it are automatically finished by the system.
> - Task information is stored only in memory. After the device restarts, the tasks are automatically finished.

**Since:** 26.1.0

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| taskId | string | Yes | Task ID, which serves as the attribution key for pulling up processes during task execution. The value ranges from 1 to 256 characters. |
| priority | [TaskPriority](#taskpriority) | No | Task priority. The default value is **MEDIUM**. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------- |
| 202 | Not System App. Interface caller is not a system app. |
| 16000301 | Task already exists. |

**Example**

```ts
import { taskManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Start the task with high priority.
  taskManager.startTask('task_001', taskManager.TaskPriority.HIGH)
    .then(() => {
      console.info('Succeeded in starting task.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to start task. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to start task. Code: ${code}, message: ${message}`);
}
```

## taskManager.finishTask

finishTask(taskId: string): Promise&lt;void&gt;

Finishes the task with the specified task ID. This API uses a promise to return the result.

After the task is finished, the system revokes the resource management applied to the process attributed to the task, and the scheduling state of the process is restored. If the task does not exist or has already been finished, error code 16000302 is returned.

> **NOTE**
>
> Only the application that created the task can finish it. If another application calls this API, error code 16000302 is returned.

**Since:** 26.1.0

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| taskId | string | Yes | Task ID, which is the task ID passed in when the task is created by calling [startTask](#taskmanagerstarttask). The value contains 1 to 256 characters. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------- |
| 202 | Not System App. Interface caller is not a system app. |
| 16000302 | Task not found. |

**Example**

```ts
import { taskManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Finish the task.
  taskManager.finishTask('task_001')
    .then(() => {
      console.info('Succeeded in finishing task.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to finish task. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to finish task. Code: ${code}, message: ${message}`);
}
```
