# DataTransferProgress

长时任务通知进度信息。

**起始版本：** 26.1.0

<!--Device-backgroundTaskManager-export interface DataTransferProgress--><!--Device-backgroundTaskManager-export interface DataTransferProgress-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## continuousTaskId

```TypeScript
continuousTaskId: int
```

长时任务ID。 取值限定为整数。

**类型：** int

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataTransferProgress-continuousTaskId: int--><!--Device-DataTransferProgress-continuousTaskId: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## progressInfo

```TypeScript
progressInfo: ProgressInfo
```

通知进度信息。

**类型：** ProgressInfo

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataTransferProgress-progressInfo: ProgressInfo--><!--Device-DataTransferProgress-progressInfo: ProgressInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

通知参数，用于指定点击长时任务通知后跳转的界面。

**类型：** [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataTransferProgress-wantAgent?: WantAgent--><!--Device-DataTransferProgress-wantAgent?: WantAgent-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

