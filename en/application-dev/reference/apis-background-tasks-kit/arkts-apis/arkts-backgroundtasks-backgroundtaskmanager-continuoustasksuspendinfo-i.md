# ContinuousTaskSuspendInfo

```TypeScript
interface ContinuousTaskSuspendInfo
```

Describes the information about a suspended continuous task.

**Since:** 20

<!--Device-backgroundTaskManager-interface ContinuousTaskSuspendInfo--><!--Device-backgroundTaskManager-interface ContinuousTaskSuspendInfo-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## continuousTaskId

```TypeScript
continuousTaskId: number
```

ID of the suspended continuous task.

**Type:** number

**Since:** 20

<!--Device-ContinuousTaskSuspendInfo-continuousTaskId: int--><!--Device-ContinuousTaskSuspendInfo-continuousTaskId: int-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## suspendMessage

```TypeScript
suspendMessage?: SuspendMessage
```

Describes the information about a suspended continuous task.

**Type:** [SuspendMessage](arkts-backgroundtasks-backgroundtaskmanager-suspendmessage-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContinuousTaskSuspendInfo-suspendMessage?: SuspendMessage--><!--Device-ContinuousTaskSuspendInfo-suspendMessage?: SuspendMessage-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## suspendReason

```TypeScript
suspendReason: ContinuousTaskSuspendReason
```

Reason why the continuous task is suspended.

**Type:** [ContinuousTaskSuspendReason](arkts-backgroundtasks-backgroundtaskmanager-continuoustasksuspendreason-e.md)

**Since:** 20

<!--Device-ContinuousTaskSuspendInfo-suspendReason: ContinuousTaskSuspendReason--><!--Device-ContinuousTaskSuspendInfo-suspendReason: ContinuousTaskSuspendReason-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## suspendState

```TypeScript
suspendState: boolean
```

Continuous task state. The value **false** indicates that the task is activated, and the value **true** indicates that the task is suspended.

**Type:** boolean

**Since:** 20

<!--Device-ContinuousTaskSuspendInfo-suspendState: boolean--><!--Device-ContinuousTaskSuspendInfo-suspendState: boolean-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
