# getRemainingDelayTime

## getRemainingDelayTime

```TypeScript
function getRemainingDelayTime(requestId: int, callback: AsyncCallback<int>): void
```

获取本次短时任务的剩余时间，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: int, callback: AsyncCallback<int>): void--><!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: int, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestId | int | 是 | 短时任务的请求ID。通过申请短时任务[requestSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-requestsuspenddelay-f.md#requestSuspendDelay) 接口获取。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 回调函数，返回本次短时任务的剩余时间，单位：ms。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt; 2. Incorrect parameters types; 3. Parameter verification failed. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9800001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800001-内存操作失败) | Memory operation failed. |
| [9900002](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9900002-短时任务校验失败) | Transient task verification failed. |
| [9800003](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800003-ipc通信失败) | Internal transaction failed. |
| [9900001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9900001-短时任务调用方信息校验失败) | Caller information verification failed for a transient task. |
| [9800002](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; &lt;br&gt; 2. Failed to apply for memory. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';

// 短时任务的请求ID，用于查询剩余时间
let requestId = 1;
backgroundTaskManager.getRemainingDelayTime(requestId, (error: BusinessError, res: number) => {
  if (error) {
    console.error(`callback => Operation getRemainingDelayTime failed. code is ${error.code} message is ${error.message}`);
  } else {
    console.info('callback => Operation getRemainingDelayTime succeeded. Data: ' + JSON.stringify(res));
  }
})
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';

// 短时任务的请求ID，用于查询剩余时间
let requestId: int = 1;
backgroundTaskManager.getRemainingDelayTime(requestId, (error: BusinessError<void> | null, res?: int) => {
  if (error) {
    console.error(`callback => Operation getRemainingDelayTime failed. code is ${error.code} message is ${error.message}`);
  } else {
    console.info('callback => Operation getRemainingDelayTime succeeded. Data: ' + JSON.stringify(res));
  }
})
```


## getRemainingDelayTime

```TypeScript
function getRemainingDelayTime(requestId: int): Promise<int>
```

获取本次短时任务的剩余时间，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: int): Promise<int>--><!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: int): Promise<int>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestId | int | 是 | 短时任务的请求ID。通过申请短时任务[requestSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-requestsuspenddelay-f.md#requestSuspendDelay) 接口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回本次短时任务的剩余时间，单位：ms。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt; 2. Incorrect parameters types; 3. Parameter verification failed. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9800001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800001-内存操作失败) | Memory operation failed. |
| [9900002](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9900002-短时任务校验失败) | Transient task verification failed. |
| [9800003](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800003-ipc通信失败) | Internal transaction failed. |
| [9900001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9900001-短时任务调用方信息校验失败) | Caller information verification failed for a transient task. |
| [9800002](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; &lt;br&gt; 2. Failed to apply for memory. |

## 示例

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';

let requestId: int = 1;
backgroundTaskManager.getRemainingDelayTime(requestId).then((res: int) => {
  console.info('promise => Operation getRemainingDelayTime succeeded. Data: ' + JSON.stringify(res));
}).catch((error) => {
  console.error(`promise => Operation getRemainingDelayTime failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
})
```

