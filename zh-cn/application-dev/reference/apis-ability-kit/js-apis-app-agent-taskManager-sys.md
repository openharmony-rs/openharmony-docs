# @ohos.app.agent.taskManager (任务管理)(系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

任务是用户意图执行的归因单元。taskManager 模块提供完整的任务生命周期管理能力，支持启动任务、结束任务等操作。任务存续期间，系统按任务优先级对归属该任务的进程进行统一的资源调度管理。

系统应用调用 startTask 接口创建并激活任务。任务可通过以下任一方式结束：
- 调用finishTask接口正常结束；
- 任务超时，由系统自动结束；
- 任务创建者进程退出，由系统自动结束。

任务结束后，系统撤销对该任务归属进程施加的资源管理，进程调度状态随之恢复。任务信息仅保存在内存中，设备重启后任务自动结束。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

> **说明：**
>
> 本模块接口均为系统接口。

## 导入模块

```ts
import { taskManager } from '@kit.AbilityKit';
```

## TaskPriority

表示任务优先级。任务启动后，系统按照该优先级对归属到任务的进程进行管理。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**模型约束**：仅可在Stage模型下使用。

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| LOW | 100 | 低优先级。 |
| MEDIUM | 200 | 中优先级。 |
| HIGH | 300 | 高优先级。 |

## taskManager.startTask

startTask(taskId: string, priority?: TaskPriority): Promise&lt;void&gt;

启动指定任务ID的任务，任务立即激活。使用Promise异步回调。

任务激活后，归属到该任务的进程由系统按指定优先级进行管理。任务在调用[finishTask](#taskmanagerfinishtask)结束或被系统自动结束（例如任务超时、创建者进程退出）前保持活跃。若指定任务ID的任务已存在，则返回错误码16000301。

> **说明：**
>
> - 任务超时时长由系统配置，任务自最后一次添加纳管进程起（无纳管进程时自创建起）无新纳管达到系统超时时间（默认 600s），每次新增纳管进程刷新超时计时，超时后任务由系统自动结束。
> - 任务创建者进程退出后，其创建的任务由系统自动结束。
> - 任务信息仅保存在内存中，设备重启后任务自动结束。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| taskId | string | 是 | 任务ID，作为任务执行期间拉起进程的归因键，取值范围为1~256个字符。 |
| priority | [TaskPriority](#taskpriority) | 否 | 任务优先级，不传入时默认为**MEDIUM**。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 202 | Not System App. Interface caller is not a system app. |
| 16000301 | Task already exists. |

**示例：**

```ts
import { taskManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 以高优先级启动任务
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

结束指定任务ID的任务。使用Promise异步回调。

任务结束后，系统撤销对该任务归属进程施加的资源管理，进程的调度状态恢复。若任务不存在或已结束，则返回错误码16000302。

> **说明：**
>
> 仅创建该任务的应用可结束该任务，其他应用调用本接口将返回错误码16000302。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| taskId | string | 是 | 任务ID，为调用[startTask](#taskmanagerstarttask)接口创建任务时传入的任务ID，取值范围为1~256个字符。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 202 | Not System App. Interface caller is not a system app. |
| 16000302 | Task not found. |

**示例：**

```ts
import { taskManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 结束任务
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
