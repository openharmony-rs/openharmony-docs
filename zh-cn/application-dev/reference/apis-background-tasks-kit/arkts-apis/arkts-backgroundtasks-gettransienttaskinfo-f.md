# getTransientTaskInfo

## getTransientTaskInfo

```TypeScript
function getTransientTaskInfo(): Promise<TransientTaskInfo>
```

获取所有短时任务信息，如当日剩余总配额等，使用Promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;TransientTaskInfo&gt; | Promise对象，返回所有短时任务信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9900001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9900001-短时任务调用方信息校验失败) | Caller information verification failed for a transient task. |
| [9900003](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9900003-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [9900004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9900004-系统服务失败) | System service operation failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  backgroundTaskManager.getTransientTaskInfo().then((res: backgroundTaskManager.TransientTaskInfo) => {
    console.info(`Operation getTransientTaskInfo succeeded. data: ` + JSON.stringify(res));
  }).catch((error : BusinessError) => {
    console.error(`Operation getTransientTaskInfo failed. code is ${error.code} message is ${error.message}`);
  });
} catch (error) {
  console.error(`Operation getTransientTaskInfo failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}

```

