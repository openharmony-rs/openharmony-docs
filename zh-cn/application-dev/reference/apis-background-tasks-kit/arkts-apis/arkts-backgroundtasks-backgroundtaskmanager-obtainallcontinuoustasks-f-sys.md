# obtainAllContinuousTasks（系统接口）

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

<a id="obtainallcontinuoustasks"></a>
## obtainAllContinuousTasks

```TypeScript
function obtainAllContinuousTasks(): Promise<ContinuousTaskInfo[]>
```

获取所有长时任务信息，如长时任务ID、长时任务类型等。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.GET_BACKGROUND_TASK_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-backgroundTaskManager-function obtainAllContinuousTasks(): Promise<ContinuousTaskInfo[]>--><!--Device-backgroundTaskManager-function obtainAllContinuousTasks(): Promise<ContinuousTaskInfo[]>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ContinuousTaskInfo[]&gt; | Promise对象，返回所有长时任务信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    // 如果当前没有申请长时任务，则获取到一个空数组
    backgroundTaskManager.obtainAllContinuousTasks().then((res: backgroundTaskManager.ContinuousTaskInfo[]) => {
        console.info(`Operation obtainAllContinuousTasks succeeded. data: ` + JSON.stringify(res));
    }).catch((error: BusinessError) => {
        console.error(`Operation obtainAllContinuousTasks failed. code is ${error.code} message is ${error.message}`);
    });
} catch (error) {
    console.error(`Operation obtainAllContinuousTasks failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}

```

