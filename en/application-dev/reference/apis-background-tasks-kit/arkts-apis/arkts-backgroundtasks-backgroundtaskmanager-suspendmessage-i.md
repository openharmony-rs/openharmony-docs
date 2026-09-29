# SuspendMessage

```TypeScript
interface SuspendMessage
```

Describes the reason why a continuous task is suspended.

**Since:** 26.0.0

<!--Device-backgroundTaskManager-interface SuspendMessage--><!--Device-backgroundTaskManager-interface SuspendMessage-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## message

```TypeScript
message: string
```

Suspension message.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SuspendMessage-message: string--><!--Device-SuspendMessage-message: string-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## reason

```TypeScript
reason: ContinuousTaskSuspendReason
```

Reason why the continuous task is suspended.

**Type:** [ContinuousTaskSuspendReason](arkts-backgroundtasks-backgroundtaskmanager-continuoustasksuspendreason-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SuspendMessage-reason: ContinuousTaskSuspendReason--><!--Device-SuspendMessage-reason: ContinuousTaskSuspendReason-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
