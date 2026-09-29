# DataTransferProgress

```TypeScript
export interface DataTransferProgress
```

Information about continuousTask notification progress.

**Since:** 26.0.1

<!--Device-backgroundTaskManager-export interface DataTransferProgress--><!--Device-backgroundTaskManager-export interface DataTransferProgress-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## continuousTaskId

```TypeScript
continuousTaskId: number
```

Continuous task ID. The value should be an integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataTransferProgress-continuousTaskId: int--><!--Device-DataTransferProgress-continuousTaskId: int-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## progressInfo

```TypeScript
progressInfo: ProgressInfo
```

Notify progress data.

**Type:** [ProgressInfo](arkts-backgroundtasks-backgroundtaskmanager-progressinfo-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataTransferProgress-progressInfo: ProgressInfo--><!--Device-DataTransferProgress-progressInfo: ProgressInfo-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

Notification parameters, which are used to specify the target page that is redirected to when a continuous task notification is clicked.

**Type:** [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataTransferProgress-wantAgent?: WantAgent--><!--Device-DataTransferProgress-wantAgent?: WantAgent-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
