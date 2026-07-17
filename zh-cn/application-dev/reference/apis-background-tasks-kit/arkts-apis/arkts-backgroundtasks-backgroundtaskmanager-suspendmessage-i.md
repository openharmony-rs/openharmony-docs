# SuspendMessage

长时任务暂停原因。

**起始版本：** 26.0.0

<!--Device-backgroundTaskManager-interface SuspendMessage--><!--Device-backgroundTaskManager-interface SuspendMessage-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## message

```TypeScript
message: string
```

长时任务暂停的信息。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SuspendMessage-message: string--><!--Device-SuspendMessage-message: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## reason

```TypeScript
reason: ContinuousTaskSuspendReason
```

长时任务暂停的原因。

**类型：** ContinuousTaskSuspendReason

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SuspendMessage-reason: ContinuousTaskSuspendReason--><!--Device-SuspendMessage-reason: ContinuousTaskSuspendReason-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

