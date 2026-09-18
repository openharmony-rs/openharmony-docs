# @ohos.WorkSchedulerExtensionAbility (Deferred Task Scheduling Callbacks)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=26a4eea6b424217513c7baf6b84329a3a2e3aeb7 translatedAt=2026-09-15T13:41:23.612Z pushedAt=2026-09-17T09:04:01.260Z -->

The **WorkSchedulerExtensionAbility** module provides callbacks for deferred task scheduling. You can override the APIs provided by this module. When a deferred task is triggered, the system calls back the application through the APIs allowing you to process the task logic in the callback.

>  **NOTE**
>
>  - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
>  - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { WorkSchedulerExtensionAbility } from '@kit.BackgroundTasksKit';
```

## Constraints
To ensure system security and stability and prevent **WorkSchedulerExtensionAbility** from abusing system resources, the system imposes certain restrictions. Importing the following modules is not supported:

  [@ohos.resourceschedule.backgroundTaskManager (Background Task Management)](./js-apis-resourceschedule-backgroundTaskManager.md)

  [@ohos.backgroundTaskManager (Background Task Management)](./js-apis-backgroundTaskManager.md)

  [@ohos.multimedia.camera (Camera Management)](../apis-camera-kit/arkts-apis-camera.md)

  [@ohos.multimedia.audio (Audio Management)](../apis-audio-kit/arkts-apis-audio.md)

  [@ohos.multimedia.media (Media)](../apis-media-kit/arkts-apis-media.md)

## WorkSchedulerExtensionContext<sup>10+</sup>

type WorkSchedulerExtensionContext = _WorkSchedulerExtensionContext

**WorkSchedulerExtensionContext** represents the context of **WorkSchedulerExtensionAbility** and inherits from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md).

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

| Type| Description|
| -------- |  -------- |
| [_WorkSchedulerExtensionContext](js-apis-WorkSchedulerExtensionContext.md)|  Context of the **WorkSchedulerExtension**.|

## WorkSchedulerExtensionAbility

Delayed task callback. When the scheduling conditions are met or the scheduling ends, the system calls back the [onWorkStart()](#onworkstart) or [onWorkStop()](#onworkstop) method in the application's WorkSchedulerExtensionAbility.

### Attributes

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| context<sup>10+</sup> | [WorkSchedulerExtensionContext](js-apis-WorkSchedulerExtensionContext.md)  | No| No| Context of the **WorkSchedulerExtensionAbility**. This context inherits from **ExtensionContext**.|

### onWorkStart

onWorkStart(work: workScheduler.WorkInfo): void

Called when the system starts scheduling the deferred task. This callback is triggered when the scheduling conditions are met.

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**Parameters**

| Name | Type                                      | Mandatory  | Description            |
| ---- | ---------------------------------------- | ---- | -------------- |
| work | [workScheduler.WorkInfo](js-apis-resourceschedule-workScheduler.md#workinfo) | Yes   | The task to be added to the execution queue.|

**Example**

```ts
import { workScheduler } from '@kit.BackgroundTasksKit';
import { WorkSchedulerExtensionAbility } from '@kit.BackgroundTasksKit';

export default class MyWorkSchedulerExtensionAbility extends WorkSchedulerExtensionAbility {
  onWorkStart(work: workScheduler.WorkInfo) {
    console.info(`MyWorkSchedulerExtensionAbility onWorkStart, workId: ${work.workId},
      bundleName: ${work.bundleName}, abilityName: ${work.abilityName}.`);
  }
}
```

### onWorkStop

onWorkStop(work: workScheduler.WorkInfo): void

Called when the system stops scheduling the deferred task. This callback is triggered when the deferred task times out for 2 minutes or the [stopWork](js-apis-resourceschedule-workScheduler.md#workschedulerstopwork) API is called to cancel the task.

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**Parameters**

| Name | Type                                      | Mandatory  | Description            |
| ---- | ---------------------------------------- | ---- | -------------- |
| work | [workScheduler.WorkInfo](js-apis-resourceschedule-workScheduler.md#workinfo) | Yes   | Task in the execution queue for which the callback is to be ended.|


**Example**

```ts
import { workScheduler } from '@kit.BackgroundTasksKit';
import { WorkSchedulerExtensionAbility } from '@kit.BackgroundTasksKit';

export default class MyWorkSchedulerExtensionAbility extends WorkSchedulerExtensionAbility {
  onWorkStop(work: workScheduler.WorkInfo) {
    console.info(`MyWorkSchedulerExtensionAbility onWorkStop, workId: ${work.workId},
      bundleName: ${work.bundleName}, abilityName: ${work.abilityName}.`);
  }
}
```