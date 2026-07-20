# BackgroundTaskSubscriber（系统接口）

后台任务监听。

**起始版本：** 23

<!--Device-backgroundTaskManager-export interface BackgroundTaskSubscriber--><!--Device-backgroundTaskManager-export interface BackgroundTaskSubscriber-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

<a id="oncontinuoustaskstart"></a>
## onContinuousTaskStart

```TypeScript
onContinuousTaskStart(info: ContinuousTaskInfo): void
```

长时任务开始回调接口。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundTaskSubscriber-onContinuousTaskStart(info: ContinuousTaskInfo): void--><!--Device-BackgroundTaskSubscriber-onContinuousTaskStart(info: ContinuousTaskInfo): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [ContinuousTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskinfo-i.md) | 是 | 长时任务回调信息，长时任务ID、长时任务类型等。 |

**示例：**

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

<a id="oncontinuoustaskstop"></a>
## onContinuousTaskStop

```TypeScript
onContinuousTaskStop(info: ContinuousTaskInfo): void
```

长时任务结束回调接口。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundTaskSubscriber-onContinuousTaskStop(info: ContinuousTaskInfo): void--><!--Device-BackgroundTaskSubscriber-onContinuousTaskStop(info: ContinuousTaskInfo): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [ContinuousTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskinfo-i.md) | 是 | 长时任务回调信息，长时任务ID、长时任务类型等。 |

**示例：**

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

<a id="oncontinuoustaskupdate"></a>
## onContinuousTaskUpdate

```TypeScript
onContinuousTaskUpdate(info: ContinuousTaskInfo): void
```

长时任务更新回调接口。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundTaskSubscriber-onContinuousTaskUpdate(info: ContinuousTaskInfo): void--><!--Device-BackgroundTaskSubscriber-onContinuousTaskUpdate(info: ContinuousTaskInfo): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [ContinuousTaskInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskinfo-i.md) | 是 | 长时任务回调信息，长时任务ID、长时任务类型等。 |

**示例：**

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

