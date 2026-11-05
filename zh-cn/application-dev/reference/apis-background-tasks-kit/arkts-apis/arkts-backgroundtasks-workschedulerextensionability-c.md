# WorkSchedulerExtensionAbility

```TypeScript
declare class WorkSchedulerExtensionAbility
```

延迟任务回调，当满足调度条件或调度结束时，系统会回调应用WorkSchedulerExtensionAbility中[onWorkStart()](#onworkstart)或[onWorkStop()](#onworkstop)的方法。

**起始版本：** 9

<!--Device-unnamed-declare class WorkSchedulerExtensionAbility--><!--Device-unnamed-declare class WorkSchedulerExtensionAbility-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## ExtensionAbility使用限制

为保障系统安全性和稳定性，防止WorkSchedulerExtensionAbility滥用系统资源，系统对其能力进行管控，不支持部分模块的引用，详情请参考[附录](#附录)。

## 导入模块

```TypeScript
import { WorkSchedulerExtensionAbility, WorkSchedulerExtensionContext } from '@kit.BackgroundTasksKit';
```

## onWorkStart

```TypeScript
onWorkStart(work: workScheduler.WorkInfo): void
```

开始延迟任务调度回调。当满足调度条件时触发该回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WorkSchedulerExtensionAbility-onWorkStart(work: workScheduler.WorkInfo): void--><!--Device-WorkSchedulerExtensionAbility-onWorkStart(work: workScheduler.WorkInfo): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| work | [workScheduler.WorkInfo](arkts-backgroundtasks-workscheduler-workinfo-i.md) | 是 | 要添加到执行队列的任务。 |

**示例**

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

结束延迟任务调度回调。当延迟任务2分钟超时或应用调用[stopWork](arkts-backgroundtasks-workscheduler-stopwork-f.md)接口取消任务时，触发该回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WorkSchedulerExtensionAbility-onWorkStop(work: workScheduler.WorkInfo): void--><!--Device-WorkSchedulerExtensionAbility-onWorkStop(work: workScheduler.WorkInfo): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| work | [workScheduler.WorkInfo](arkts-backgroundtasks-workscheduler-workinfo-i.md) | 是 | 执行队列中要结束回调的任务。 |

**示例**

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

WorkSchedulerExtension的上下文环境，继承自ExtensionContext。

**类型：** [WorkSchedulerExtensionContext](arkts-backgroundtasks-workschedulerextensioncontext-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WorkSchedulerExtensionAbility-context: WorkSchedulerExtensionContext--><!--Device-WorkSchedulerExtensionAbility-context: WorkSchedulerExtensionContext-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## 附录

WorkSchedulerExtensionAbility不支持以下模块的引用。

| Kit | 模块 |
| --- | --- |
| Background Tasks Kit | [@ohos.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager.md) |
| Background Tasks Kit | [@ohos.resourceschedule.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-backgroundtaskmanager.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
