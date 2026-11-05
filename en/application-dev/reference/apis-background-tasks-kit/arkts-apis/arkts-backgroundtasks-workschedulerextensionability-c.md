# WorkSchedulerExtensionAbility

```TypeScript
declare class WorkSchedulerExtensionAbility
```

Provides callbacks to be invoked when the scheduling conditions are met or the scheduling ends, for example, [onWorkStart()](#onworkstart) or [onWorkStop()](#onworkstop) in WorkSchedulerExtensionAbility.

**Since:** 9

<!--Device-unnamed-declare class WorkSchedulerExtensionAbility--><!--Device-unnamed-declare class WorkSchedulerExtensionAbility-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

## ExtensionAbility Usage Restrictions

To ensure system security and stability, WorkSchedulerExtensionAbility is restricted from abusing system resources. The system controls its capabilities and does not support referencing some modules. For details, see [Appendix](#appendix).

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

## Appendix

WorkSchedulerExtensionAbility does not support referencing the following modules.

| Kit | Module |
| --- | --- |
| Background Tasks Kit | [@ohos.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager.md) |
| Background Tasks Kit | [@ohos.resourceschedule.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-backgroundtaskmanager.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
