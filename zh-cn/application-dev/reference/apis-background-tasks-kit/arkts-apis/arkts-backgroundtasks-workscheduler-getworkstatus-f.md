# getWorkStatus

## 导入模块

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## getWorkStatus

```TypeScript
function getWorkStatus(workId: number, callback: AsyncCallback<WorkInfo>): void
```

通过workId获取延迟任务，使用Callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| workId | number | 是 | 延迟任务Id。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WorkInfo](arkts-backgroundtasks-workscheduler-workinfo-i.md)&gt; | 是 | 回调函数。如果workId有效，则返回从WorkSchedulerService获取的任务，否则抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: Parameter verification failed. |
| [9700001](../errorcode-workScheduler.md#9700001-内存操作失败) | Memory operation failed. |
| [9700002](../errorcode-workScheduler.md#9700002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| [9700003](../errorcode-workScheduler.md#9700003-系统服务失败) | System service operation failed. |
| [9700004](../errorcode-workScheduler.md#9700004-参数校验失败) | Check on workInfo failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { workScheduler } from '@kit.BackgroundTasksKit';

workScheduler.getWorkStatus(50, (error: BusinessError, res: workScheduler.WorkInfo) => {
  if (error) {
    console.error(`workschedulerLog getWorkStatus failed. code is ${error.code} message is ${error.message}`);
  } else {
    console.info(`workschedulerLog getWorkStatus success, ${JSON.stringify(res)}`);
  }
});
```


## getWorkStatus

```TypeScript
function getWorkStatus(workId: number): Promise<WorkInfo>
```

通过workId获取延迟任务，使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| workId | number | 是 | 延迟任务Id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[WorkInfo](arkts-backgroundtasks-workscheduler-workinfo-i.md)&gt; | Promise对象，如果workId有效，则返回从WorkSchedulerService获取的任务，否则抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: Parameter verification failed. |
| [9700001](../errorcode-workScheduler.md#9700001-内存操作失败) | Memory operation failed. |
| [9700002](../errorcode-workScheduler.md#9700002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| [9700003](../errorcode-workScheduler.md#9700003-系统服务失败) | System service operation failed. |
| [9700004](../errorcode-workScheduler.md#9700004-参数校验失败) | Check on workInfo failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { workScheduler } from '@kit.BackgroundTasksKit';

workScheduler.getWorkStatus(50).then((res: workScheduler.WorkInfo) => {
  console.info(`workschedulerLog getWorkStatus success, ${JSON.stringify(res)}`);
}).catch((error: BusinessError) => {
  console.error(`workschedulerLog getWorkStatus failed. code is ${error.code} message is ${error.message}`);
})
```
