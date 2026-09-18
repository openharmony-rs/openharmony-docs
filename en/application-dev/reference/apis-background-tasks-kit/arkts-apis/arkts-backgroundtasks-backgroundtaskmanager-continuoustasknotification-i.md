# ContinuousTaskNotification

Describes the information about a continuous-task notification.

**Since:** 12

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## contentType

```TypeScript
contentType: notificationManager.ContentType
```

Content type of a continuous-task notification.

**Type:** [notificationManager.ContentType](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager-contenttype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## continuousTaskId

```TypeScript
continuousTaskId?: number
```

ID of a continuous task.

**Type:** number

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## notificationId

```TypeScript
notificationId: number
```

ID of the continuous-task notification.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## slotType

```TypeScript
slotType: notificationManager.SlotType
```

Slot type of a continuous-task notification.

Note: After a continuous task is successfully requested or updated, no prompt tone is played.

**Type:** [notificationManager.SlotType](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager-slottype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask
