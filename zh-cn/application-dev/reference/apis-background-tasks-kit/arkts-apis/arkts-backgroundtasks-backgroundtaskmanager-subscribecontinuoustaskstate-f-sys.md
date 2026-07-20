# subscribeContinuousTaskState（系统接口）

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

<a id="subscribecontinuoustaskstate"></a>
## subscribeContinuousTaskState

```TypeScript
function subscribeContinuousTaskState(subscriber: BackgroundTaskSubscriber): void
```

注册长时任务变化回调。

**起始版本：** 23

**需要权限：** ohos.permission.GET_BACKGROUND_TASK_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-backgroundTaskManager-function subscribeContinuousTaskState(subscriber: BackgroundTaskSubscriber): void--><!--Device-backgroundTaskManager-function subscribeContinuousTaskState(subscriber: BackgroundTaskSubscriber): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriber | [BackgroundTaskSubscriber](arkts-backgroundtasks-backgroundtaskmanager-backgroundtasksubscriber-i-sys.md) | 是 | 后台任务监听对象，包含长时任务开始，长时任务更新，长时任务结束。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

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

try {
    backgroundTaskManager.subscribeContinuousTaskState(backgroundTaskSubscriber);
    console.info('Operation subscribeContinuousTaskState succeeded');
} catch (error) {
    console.error(`Operation subscribeContinuousTaskState failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}

```

