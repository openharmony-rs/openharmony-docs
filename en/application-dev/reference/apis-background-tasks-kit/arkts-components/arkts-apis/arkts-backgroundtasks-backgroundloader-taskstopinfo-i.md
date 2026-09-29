# TaskStopInfo

```TypeScript
export interface TaskStopInfo
```

Represents the background load task stop information, which is used to ON_STOP function.

**Since:** 26.2.0

<!--Device-backgroundLoader-export interface TaskStopInfo--><!--Device-backgroundLoader-export interface TaskStopInfo-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

## Modules to Import

```TypeScript
import { backgroundLoader } from '@kit.BackgroundTasksKit';
```

## abilityName

```TypeScript
abilityName: string
```

Ability name in the bundle.

**Type:** string

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TaskStopInfo-abilityName: string--><!--Device-TaskStopInfo-abilityName: string-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

## stopCode

```TypeScript
stopCode: StopCode
```

Stop code.

**Type:** [StopCode](arkts-backgroundtasks-backgroundloader-stopcode-e.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TaskStopInfo-stopCode: StopCode--><!--Device-TaskStopInfo-stopCode: StopCode-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

## stopMessage

```TypeScript
stopMessage: string
```

Stop message.

**Type:** string

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TaskStopInfo-stopMessage: string--><!--Device-TaskStopInfo-stopMessage: string-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

## taskId

```TypeScript
taskId: number
```

Id of the background load task.

**Type:** number

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TaskStopInfo-taskId: int--><!--Device-TaskStopInfo-taskId: int-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler
