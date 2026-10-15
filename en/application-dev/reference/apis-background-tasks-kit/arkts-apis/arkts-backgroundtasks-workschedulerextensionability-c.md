# WorkSchedulerExtensionAbility

```TypeScript
declare class WorkSchedulerExtensionAbility
```

Provides callbacks to be invoked when the scheduling conditions are met or the scheduling ends, for example, [onWorkStart()](#onworkstart) or [onWorkStop()](#onworkstop) in WorkSchedulerExtensionAbility.

**Since:** 9

<!--Device-unnamed-declare class WorkSchedulerExtensionAbility--><!--Device-unnamed-declare class WorkSchedulerExtensionAbility-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

## Modules to Import

```TypeScript
import { WorkSchedulerExtensionAbility, WorkSchedulerExtensionContext } from '@kit.BackgroundTasksKit';
```

## onWorkStart

```TypeScript
onWorkStart(work: workScheduler.WorkInfo): void
```

Called when the system starts scheduling the deferred task.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-WorkSchedulerExtensionAbility-onWorkStart(work: workScheduler.WorkInfo): void--><!--Device-WorkSchedulerExtensionAbility-onWorkStart(work: workScheduler.WorkInfo): void-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| work | [workScheduler.WorkInfo](arkts-backgroundtasks-workscheduler-workinfo-i.md) | Yes | Deferred task that starts. |

**Examples**

```TypeScript
import { WorkSchedulerExtensionAbility, workScheduler } from '@kit.BackgroundTasksKit';

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

Called when the system stops scheduling the deferred task. This callback is triggered when the deferred task times out for 2 minutes or the [stopWork](arkts-backgroundtasks-workscheduler-stopwork-f.md) API is called to cancel the task.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-WorkSchedulerExtensionAbility-onWorkStop(work: workScheduler.WorkInfo): void--><!--Device-WorkSchedulerExtensionAbility-onWorkStop(work: workScheduler.WorkInfo): void-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| work | [workScheduler.WorkInfo](arkts-backgroundtasks-workscheduler-workinfo-i.md) | Yes | Deferred task that stops. |

**Examples**

```TypeScript
import { WorkSchedulerExtensionAbility, workScheduler } from '@kit.BackgroundTasksKit';

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

Context of the WorkSchedulerExtensionAbility. This context inherits from ExtensionContext.

**Type:** [WorkSchedulerExtensionContext](arkts-backgroundtasks-workschedulerextensioncontext-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-WorkSchedulerExtensionAbility-context: WorkSchedulerExtensionContext--><!--Device-WorkSchedulerExtensionAbility-context: WorkSchedulerExtensionContext-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler
