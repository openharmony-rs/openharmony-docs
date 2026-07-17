# ContinuousTaskNotification

长时任务通知信息。

**起始版本：** 12

<!--Device-backgroundTaskManager-interface ContinuousTaskNotification--><!--Device-backgroundTaskManager-interface ContinuousTaskNotification-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## contentType

```TypeScript
contentType: notificationManager.ContentType
```

长时任务通知的内容类型。

**类型：** notificationManager.ContentType

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ContinuousTaskNotification-contentType: notificationManager.ContentType--><!--Device-ContinuousTaskNotification-contentType: notificationManager.ContentType-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## continuousTaskId

```TypeScript
continuousTaskId?: number
```

长时任务 Id。

**类型：** number

**起始版本：** 15

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContinuousTaskNotification-continuousTaskId?: int--><!--Device-ContinuousTaskNotification-continuousTaskId?: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## notificationId

```TypeScript
notificationId: number
```

长时任务通知 Id。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ContinuousTaskNotification-notificationId: int--><!--Device-ContinuousTaskNotification-notificationId: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## slotType

```TypeScript
slotType: notificationManager.SlotType
```

长时任务通知的渠道类型。

**说明：** 长时任务申请或更新成功后不支持提示音。

**类型：** notificationManager.SlotType

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ContinuousTaskNotification-slotType: notificationManager.SlotType--><!--Device-ContinuousTaskNotification-slotType: notificationManager.SlotType-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

