# getRemainingDelayTime

## getRemainingDelayTime

```TypeScript
function getRemainingDelayTime(requestId: number, callback: AsyncCallback<number>): void
```

获取本次短时任务的剩余时间，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getRemainingDelayTime(requestId:

<!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: number, callback: AsyncCallback<number>): void--><!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: number, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestId | number | 是 | 延迟挂起的请求ID。这个值通过调用[requestSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-requestsuspenddelay-depr-f.md#requestsuspenddelay-1)方法获取。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数，返回本次短时任务的剩余时间，单位：ms。 |

**示例：**

```TypeScript
import backgroundTaskManager from '@ohos.backgroundTaskManager';
import { BusinessError } from '@ohos.base';

let delayInfo = backgroundTaskManager.requestSuspendDelay('test', () => {});
backgroundTaskManager.getRemainingDelayTime(delayInfo.requestId, (err: BusinessError, res: number) => {
  if (err) {
    console.error(`callback => Operation getRemainingDelayTime failed. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('callback => Operation getRemainingDelayTime succeeded. Data: ' + JSON.stringify(res));
  }
});

```


## getRemainingDelayTime

```TypeScript
function getRemainingDelayTime(requestId: number): Promise<number>
```

获取本次短时任务的剩余时间，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getRemainingDelayTime(requestId:

<!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: number): Promise<number>--><!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: number): Promise<number>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestId | number | 是 | 延迟挂起的请求ID。这个值通过调用[requestSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-requestsuspenddelay-depr-f.md#requestsuspenddelay-1)方法获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回本次短时任务的剩余时间，单位：ms。 |

**示例：**

```TypeScript
import backgroundTaskManager from '@ohos.backgroundTaskManager';
import { BusinessError } from '@ohos.base';

let delayInfo = backgroundTaskManager.requestSuspendDelay('test', () => {});
backgroundTaskManager.getRemainingDelayTime(delayInfo.requestId).then((res:number) => {
  console.info('promise => Operation getRemainingDelayTime succeeded. Data: ' + JSON.stringify(res));
}).catch((err : BusinessError) => {
  console.info(`promise => Operation getRemainingDelayTime failed. Code: ${err.code}, message: ${err.message}`);
});

```

