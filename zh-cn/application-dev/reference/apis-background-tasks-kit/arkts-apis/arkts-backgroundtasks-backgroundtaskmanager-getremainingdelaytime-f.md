# getRemainingDelayTime

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## getRemainingDelayTime

```TypeScript
function getRemainingDelayTime(requestId: number, callback: AsyncCallback<number>): void
```

获取本次短时任务的剩余时间，使用callback异步回调。

**起始版本：** 9

<!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: int, callback: AsyncCallback<int>): void--><!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: int, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestId | number | 是 | 短时任务的请求ID。通过申请短时任务[requestSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-requestsuspenddelay-f.md#requestsuspenddelay-1)接口获取。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数，返回本次短时任务的剩余时间，单位：ms。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameters types; 3. Parameter verification failed. |
| [9800001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800001-内存操作失败) | Memory operation failed. |
| [9800002](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [9800003](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800003-ipc通信失败) | Internal transaction failed. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9900001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9900001-短时任务调用方信息校验失败) | Caller information verification failed for a transient task. |
| [9900002](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9900002-短时任务校验失败) | Transient task verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';

let requestId = 1;
backgroundTaskManager.getRemainingDelayTime(requestId, (error: BusinessError, res: number) => {
  if(error) {
    console.error(`callback => Operation getRemainingDelayTime failed. code is ${error.code} message is ${error.message}`);
  } else {
    console.info('callback => Operation getRemainingDelayTime succeeded. Data: ' + JSON.stringify(res));
  }
})

```


## getRemainingDelayTime

```TypeScript
function getRemainingDelayTime(requestId: number): Promise<number>
```

获取本次短时任务的剩余时间，使用Promise异步回调。

**起始版本：** 9

<!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: int): Promise<int>--><!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: int): Promise<int>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestId | number | 是 | 短时任务的请求ID。通过申请短时任务[requestSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-requestsuspenddelay-f.md#requestsuspenddelay-1)接口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回本次短时任务的剩余时间，单位：ms。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameters types; 3. Parameter verification failed. |
| [9800001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800001-内存操作失败) | Memory operation failed. |
| [9800002](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [9800003](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800003-ipc通信失败) | Internal transaction failed. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9900001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9900001-短时任务调用方信息校验失败) | Caller information verification failed for a transient task. |
| [9900002](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9900002-短时任务校验失败) | Transient task verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';

let requestId = 1;
backgroundTaskManager.getRemainingDelayTime(requestId).then((res: number) => {
  console.info('promise => Operation getRemainingDelayTime succeeded. Data: ' + JSON.stringify(res));
}).catch((error: BusinessError) => {
  console.error(`promise => Operation getRemainingDelayTime failed. code is ${error.code} message is ${error.message}`);
})

```

