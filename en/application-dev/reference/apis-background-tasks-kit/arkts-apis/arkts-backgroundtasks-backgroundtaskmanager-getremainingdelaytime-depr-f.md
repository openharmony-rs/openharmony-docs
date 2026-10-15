# getRemainingDelayTime

## Modules to Import

```TypeScript
```

<a id="getremainingdelaytime1"></a>

## getRemainingDelayTime

```TypeScript
function getRemainingDelayTime(requestId: number, callback: AsyncCallback<number>): void
```

Obtains the remaining duration before the application is suspended. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getRemainingDelayTime](arkts-backgroundtasks-backgroundtaskmanager-getremainingdelaytime-f.md)(requestId: number, callback: AsyncCallback&lt;number&gt;)

<!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: number, callback: AsyncCallback<number>): void--><!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: number, callback: AsyncCallback<number>): void-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| requestId | number | Yes | ID of the suspension delay request. The value is obtained by calling [requestSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-requestsuspenddelay-depr-f.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the remaining duration before the application is suspended, in milliseconds. |

**Examples**

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


<a id="getremainingdelaytime2"></a>

## getRemainingDelayTime

```TypeScript
function getRemainingDelayTime(requestId: number): Promise<number>
```

Obtains the remaining duration before the application is suspended. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getRemainingDelayTime](arkts-backgroundtasks-backgroundtaskmanager-getremainingdelaytime-f.md)(requestId: number)

<!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: number): Promise<number>--><!--Device-backgroundTaskManager-function getRemainingDelayTime(requestId: number): Promise<number>-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| requestId | number | Yes | ID of the suspension delay request. The value is obtained by calling [requestSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-requestsuspenddelay-depr-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the remaining duration before the application is suspended, in milliseconds. |

**Examples**

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
