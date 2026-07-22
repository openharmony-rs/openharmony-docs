# WorkSchedulerExtensionAbility

延迟任务回调，当满足调度条件或调度结束时，系统会回调应用WorkSchedulerExtensionAbility中[onWorkStart()](arkts-backgroundtasks-workschedulerextensionability-c.md#onworkstart)或[onWorkStop()](arkts-backgroundtasks-workschedulerextensionability-c.md#onworkstop)的方法。

**起始版本：** 9

<!--Device-unnamed-declare class WorkSchedulerExtensionAbility--><!--Device-unnamed-declare class WorkSchedulerExtensionAbility-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## 导入模块

```TypeScript
import { WorkSchedulerExtensionContext } from '@kit.BackgroundTasksKit';
```

## onWorkStart

```TypeScript
onWorkStart(work: workScheduler.WorkInfo): void
```

开始延迟任务调度回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WorkSchedulerExtensionAbility-onWorkStart(work: workScheduler.WorkInfo): void--><!--Device-WorkSchedulerExtensionAbility-onWorkStart(work: workScheduler.WorkInfo): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| work | workScheduler.WorkInfo | 是 | 要添加到执行队列的任务。 |

**示例：**

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';
import { WorkSchedulerExtensionAbility } from '@kit.BackgroundTasksKit';

export default class MyWorkSchedulerExtensionAbility extends WorkSchedulerExtensionAbility {
  onWorkStart(work: workScheduler.WorkInfo) {
    console.info(`MyWorkSchedulerExtensionAbility onWorkStart, workId: ${work.workId},
      bundleName: ${work.bundleName}, abilityName: ${work.abilityName}.`);
  }
}

```

## onWorkStop

```TypeScript
onWorkStop(work: workScheduler.WorkInfo): void
```

结束延迟任务调度回调。当延迟任务2分钟超时或应用调用[stopWork](arkts-backgroundtasks-workscheduler-stopwork-f.md#stopwork)接口取消任务时，触发该回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WorkSchedulerExtensionAbility-onWorkStop(work: workScheduler.WorkInfo): void--><!--Device-WorkSchedulerExtensionAbility-onWorkStop(work: workScheduler.WorkInfo): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| work | workScheduler.WorkInfo | 是 | 执行队列中要结束回调的任务。 |

**示例：**

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';
import { WorkSchedulerExtensionAbility } from '@kit.BackgroundTasksKit';

export default class MyWorkSchedulerExtensionAbility extends WorkSchedulerExtensionAbility {
  onWorkStop(work: workScheduler.WorkInfo) {
    console.info(`MyWorkSchedulerExtensionAbility onWorkStop, workId: ${work.workId},
      bundleName: ${work.bundleName}, abilityName: ${work.abilityName}.`);
  }
}

```

## context

```TypeScript
context: WorkSchedulerExtensionContext
```

WorkSchedulerExtension的上下文环境，继承自ExtensionContext。

**类型：** WorkSchedulerExtensionContext

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WorkSchedulerExtensionAbility-context: WorkSchedulerExtensionContext--><!--Device-WorkSchedulerExtensionAbility-context: WorkSchedulerExtensionContext-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

