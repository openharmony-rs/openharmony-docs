# ContinuousTaskSuspendInfo

长时任务暂停信息。

**起始版本：** 20

<!--Device-backgroundTaskManager-interface ContinuousTaskSuspendInfo--><!--Device-backgroundTaskManager-interface ContinuousTaskSuspendInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## continuousTaskId

```TypeScript
continuousTaskId: number
```

被暂停的长时任务 Id。

**类型：** number

**起始版本：** 20

<!--Device-ContinuousTaskSuspendInfo-continuousTaskId: int--><!--Device-ContinuousTaskSuspendInfo-continuousTaskId: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## suspendMessage

```TypeScript
suspendMessage?: SuspendMessage
```

长时任务暂停信息。

**类型：** SuspendMessage

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinuousTaskSuspendInfo-suspendMessage?: SuspendMessage--><!--Device-ContinuousTaskSuspendInfo-suspendMessage?: SuspendMessage-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## suspendReason

```TypeScript
suspendReason: ContinuousTaskSuspendReason
```

长时任务暂停原因。

**类型：** ContinuousTaskSuspendReason

**起始版本：** 20

<!--Device-ContinuousTaskSuspendInfo-suspendReason: ContinuousTaskSuspendReason--><!--Device-ContinuousTaskSuspendInfo-suspendReason: ContinuousTaskSuspendReason-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## suspendState

```TypeScript
suspendState: boolean
```

长时任务状态，false表示激活，true表示暂停。

**类型：** boolean

**起始版本：** 20

<!--Device-ContinuousTaskSuspendInfo-suspendState: boolean--><!--Device-ContinuousTaskSuspendInfo-suspendState: boolean-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

