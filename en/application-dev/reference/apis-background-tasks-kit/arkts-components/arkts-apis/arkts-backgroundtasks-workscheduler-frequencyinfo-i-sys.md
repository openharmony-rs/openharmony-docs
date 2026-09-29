# FrequencyInfo (System API)

```TypeScript
export interface FrequencyInfo
```

Execution frequency information.

**Since:** 26.0.1

<!--Device-workScheduler-export interface FrequencyInfo--><!--Device-workScheduler-export interface FrequencyInfo-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## interval

```TypeScript
interval: number
```

Set app exec interval, in milliseconds. Unit:ms.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-FrequencyInfo-interval: int--><!--Device-FrequencyInfo-interval: int-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

App uid. The value should be an integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-FrequencyInfo-uid: int--><!--Device-FrequencyInfo-uid: int-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**System API:** This is a system API.

## workId

```TypeScript
workId: number
```

ID of the deferred task. The value should be an integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-FrequencyInfo-workId: int--><!--Device-FrequencyInfo-workId: int-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**System API:** This is a system API.
