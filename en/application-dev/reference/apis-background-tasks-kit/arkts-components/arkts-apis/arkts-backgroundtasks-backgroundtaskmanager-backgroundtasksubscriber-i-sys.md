# BackgroundTaskSubscriber (System API)

```TypeScript
export interface BackgroundTaskSubscriber
```

Represents a listener object used to listen for background task state changes.

**Since:** 23

<!--Device-backgroundTaskManager-export interface BackgroundTaskSubscriber--><!--Device-backgroundTaskManager-export interface BackgroundTaskSubscriber-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## onContinuousTaskStart

```TypeScript
onContinuousTaskStart(info: ContinuousTaskInfo): void
```

Called when a continuous task starts.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackgroundTaskSubscriber-onContinuousTaskStart(info: ContinuousTaskInfo): void--><!--Device-BackgroundTaskSubscriber-onContinuousTaskStart(info: ContinuousTaskInfo): void-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [ContinuousTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskinfo-i.md) | Yes | Continuous task callback information, including the task ID and type. |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';

let backgroundTaskSubscriber : backgroundTaskManager.BackgroundTaskSubscriber = {
    onContinuousTaskStart: (info: backgroundTaskManager.ContinuousTaskInfo): void => {
        console.info('Operation onContinuousTaskStart succeeded. data: ' + JSON.stringify(info));
    },
    onContinuousTaskUpdate: (info: backgroundTaskManager.ContinuousTaskInfo): void => {
        console.info('Operation onContinuousTaskUpdate succeeded. data: ' + JSON.stringify(info));
    },
    onContinuousTaskStop: (info: backgroundTaskManager.ContinuousTaskInfo): void => {
        console.info('Operation onContinuousTaskStop succeeded. data: ' + JSON.stringify(info));
    }
}
```

## onContinuousTaskStop

```TypeScript
onContinuousTaskStop(info: ContinuousTaskInfo): void
```

Called when a continuous task stops.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackgroundTaskSubscriber-onContinuousTaskStop(info: ContinuousTaskInfo): void--><!--Device-BackgroundTaskSubscriber-onContinuousTaskStop(info: ContinuousTaskInfo): void-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [ContinuousTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskinfo-i.md) | Yes | Continuous task callback information, including the task ID and type. |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';

let backgroundTaskSubscriber : backgroundTaskManager.BackgroundTaskSubscriber = {
    onContinuousTaskStart: (info: backgroundTaskManager.ContinuousTaskInfo): void => {
        console.info('Operation onContinuousTaskStart succeeded. data: ' + JSON.stringify(info));
    },
    onContinuousTaskUpdate: (info: backgroundTaskManager.ContinuousTaskInfo): void => {
        console.info('Operation onContinuousTaskUpdate succeeded. data: ' + JSON.stringify(info));
    },
    onContinuousTaskStop: (info: backgroundTaskManager.ContinuousTaskInfo): void => {
        console.info('Operation onContinuousTaskStop succeeded. data: ' + JSON.stringify(info));
    }
}
```

## onContinuousTaskUpdate

```TypeScript
onContinuousTaskUpdate(info: ContinuousTaskInfo): void
```

Called when a continuous task is updated.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackgroundTaskSubscriber-onContinuousTaskUpdate(info: ContinuousTaskInfo): void--><!--Device-BackgroundTaskSubscriber-onContinuousTaskUpdate(info: ContinuousTaskInfo): void-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [ContinuousTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskinfo-i.md) | Yes | Continuous task callback information, including the task ID and type. |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';

let backgroundTaskSubscriber : backgroundTaskManager.BackgroundTaskSubscriber = {
    onContinuousTaskStart: (info: backgroundTaskManager.ContinuousTaskInfo): void => {
        console.info('Operation onContinuousTaskStart succeeded. data: ' + JSON.stringify(info));
    },
    onContinuousTaskUpdate: (info: backgroundTaskManager.ContinuousTaskInfo): void => {
        console.info('Operation onContinuousTaskUpdate succeeded. data: ' + JSON.stringify(info));
    },
    onContinuousTaskStop: (info: backgroundTaskManager.ContinuousTaskInfo): void => {
        console.info('Operation onContinuousTaskStop succeeded. data: ' + JSON.stringify(info));
    }
}
```
