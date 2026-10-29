# CommonEventSubscriber

```TypeScript
export interface CommonEventSubscriber
```

The **CommonEventSubscriber** module provides APIs for describing the common event subscriber. The **CommonEventSubscriber** module provides the capabilities for processing [ordered common events](../../../basic-services/common-event/common-event-glossary.md#ordered-common-event), including obtaining and setting the code and data transferred by events, checking whether the current common event is an ordered or [sticky common event](../../../basic-services/common-event/common-event-glossary.md#sticky-common-event), terminating an ordered common event or clearing the termination status, ending the processing of the current ordered common event, and obtaining subscription information of a subscriber. This module is applicable to data processing and process control of the received common event by the subscriber.

**Since:** 7

<!--Device-unnamed-export interface CommonEventSubscriber--><!--Device-unnamed-export interface CommonEventSubscriber-End-->

**System capability:** SystemCapability.Notification.CommonEvent

## abortCommonEvent

```TypeScript
abortCommonEvent(callback: AsyncCallback<void>): void
```

Aborts an ordered common event. This API is used with [finishCommonEvent](#finishcommonevent-1). After the abort, the common event is not sent to the next subscriber. This API uses an asynchronous callback to return the result.

**Since:** 7

<!--Device-CommonEventSubscriber-abortCommonEvent(callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-abortCommonEvent(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.abortCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in aborting common event.`);
});
subscriber.finishCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

## abortCommonEvent

```TypeScript
abortCommonEvent(): Promise<void>
```

Aborts an ordered common event. This API is used with [finishCommonEvent](#finishcommonevent-1). After the abort, the common event is not sent to the next subscriber. This API uses a promise to return the result.

**Since:** 7

<!--Device-CommonEventSubscriber-abortCommonEvent(): Promise<void>--><!--Device-CommonEventSubscriber-abortCommonEvent(): Promise<void>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
subscriber.abortCommonEvent().then(() => {
  console.info(`Succeeded in aborting common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to abort common event. Code is ${err.code}, message is ${err.message}`);
});
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

## abortCommonEventSync

```TypeScript
abortCommonEventSync(): void
```

Aborts an ordered common event synchronously. This API is used with [finishCommonEvent](#finishcommonevent-1). After the abort, the common event is not sent to the next subscriber.

**Since:** 10

<!--Device-CommonEventSubscriber-abortCommonEventSync(): void--><!--Device-CommonEventSubscriber-abortCommonEventSync(): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Examples**

```TypeScript
subscriber.abortCommonEventSync();
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

## clearAbortCommonEvent

```TypeScript
clearAbortCommonEvent(callback: AsyncCallback<void>): void
```

Clears the abort state of an ordered common event. Use this API together with [finishCommonEvent](#finishcommonevent-1), and the common event can be passed to the next subscriber. This API uses an asynchronous callback to return the result.

**Since:** 7

<!--Device-CommonEventSubscriber-clearAbortCommonEvent(callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-clearAbortCommonEvent(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.clearAbortCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to clear abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in clearing abort common event.`);
});
subscriber.finishCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

## clearAbortCommonEvent

```TypeScript
clearAbortCommonEvent(): Promise<void>
```

Clears the abort state of an ordered common event. Use this API together with [finishCommonEvent](#finishcommonevent-1), and the common event can be passed to the next subscriber. This API uses a promise to return the result.

**Since:** 7

<!--Device-CommonEventSubscriber-clearAbortCommonEvent(): Promise<void>--><!--Device-CommonEventSubscriber-clearAbortCommonEvent(): Promise<void>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
subscriber.clearAbortCommonEvent().then(() => {
  console.info(`Succeeded in clearing abort common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to clear abort common event. Code is ${err.code}, message is ${err.message}`);
});
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

## clearAbortCommonEventSync

```TypeScript
clearAbortCommonEventSync(): void
```

Clears the abort state of an ordered common event synchronously. Use this API together with [finishCommonEvent](#finishcommonevent-1), and the common event can be passed to the next subscriber.

**Since:** 10

<!--Device-CommonEventSubscriber-clearAbortCommonEventSync(): void--><!--Device-CommonEventSubscriber-clearAbortCommonEventSync(): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Examples**

```TypeScript
subscriber.clearAbortCommonEventSync();
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

## finishCommonEvent

```TypeScript
finishCommonEvent(callback: AsyncCallback<void>): void
```

Finishes this ordered common event. This API uses an asynchronous callback to return the result.

**Since:** 9

<!--Device-CommonEventSubscriber-finishCommonEvent(callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-finishCommonEvent(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.finishCommonEvent((err: BusinessError) => {
  if (err) {
    console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in finishing common event.`);
});
```

## finishCommonEvent

```TypeScript
finishCommonEvent(): Promise<void>
```

Finishes this ordered common event. This API uses a promise to return the result.

**Since:** 9

<!--Device-CommonEventSubscriber-finishCommonEvent(): Promise<void>--><!--Device-CommonEventSubscriber-finishCommonEvent(): Promise<void>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
subscriber.finishCommonEvent().then(() => {
  console.info(`Succeeded in finishing common event.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to finish common event. Code is ${err.code}, message is ${err.message}`);
});
```

## getAbortCommonEvent

```TypeScript
getAbortCommonEvent(callback: AsyncCallback<boolean>): void
```

Checks whether this ordered common event should be aborted. This API uses an asynchronous callback to return the result.

**Since:** 7

<!--Device-CommonEventSubscriber-getAbortCommonEvent(callback: AsyncCallback<boolean>): void--><!--Device-CommonEventSubscriber-getAbortCommonEvent(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the query is successful, **err** is **undefined**. If **data** is **true**, the ordered common event is aborted. If **data** is **false**, the ordered common event is not aborted. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.getAbortCommonEvent((err: BusinessError, abortEvent: boolean) => {
  if (err) {
    console.error(`Failed to get abort common event. Code is ${err.code}, message is ${err.message}`);
    return;
  } 
  console.info(`Succeeded in getting abort common event, abortEvent is ${JSON.stringify(abortEvent)}`);
});
```

## getAbortCommonEvent

```TypeScript
getAbortCommonEvent(): Promise<boolean>
```

Checks whether this ordered common event should be aborted. This API uses a promise to return the result.

**Since:** 7

<!--Device-CommonEventSubscriber-getAbortCommonEvent(): Promise<boolean>--><!--Device-CommonEventSubscriber-getAbortCommonEvent(): Promise<boolean>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. Returns **true** if the ordered common event is in the abort state; returns **false** otherwise. |

**Examples**

```TypeScript
subscriber.getAbortCommonEvent().then((abortEvent: boolean) => {
  console.info(`Succeeded in getting abort common event, abortEvent is ${JSON.stringify(abortEvent)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get abort common event. Code is ${err.code}, message is ${err.message}`);
});
```

## getAbortCommonEventSync

```TypeScript
getAbortCommonEventSync(): boolean
```

Checks whether an ordered common event is aborted synchronously.

**Since:** 10

<!--Device-CommonEventSubscriber-getAbortCommonEventSync(): boolean--><!--Device-CommonEventSubscriber-getAbortCommonEventSync(): boolean-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the ordered common event is in the abort state; returns **false** otherwise. |

**Examples**

```TypeScript
let abortEvent: boolean = subscriber.getAbortCommonEventSync();
console.info(`Succeeded in getting abort common event, abortEvent is ${JSON.stringify(abortEvent)}`);
```

## getCode

```TypeScript
getCode(callback: AsyncCallback<number>): void
```

Obtains the result code of an ordered common event. This API uses an asynchronous callback to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-getCode(callback: AsyncCallback<int>): void--><!--Device-CommonEventSubscriber-getCode(callback: AsyncCallback<int>): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the result data of an ordered common event is successfully obtained, **err** is **undefined**, and **data** is the data obtained; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.getCode((err: BusinessError, code: number) => {
  if (err) {
    console.error(`Failed to get code. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
});
```

## getCode

```TypeScript
getCode(): Promise<number>
```

Obtains the result code of an ordered common event. This API uses a promise to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-getCode(): Promise<int>--><!--Device-CommonEventSubscriber-getCode(): Promise<int>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result code of an ordered common event. |

**Examples**

```TypeScript
subscriber.getCode().then((code: number) => {
  console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get code. Code is ${err.code}, message is ${err.message}`);
});
```

## getCodeSync

```TypeScript
getCodeSync(): number
```

Obtains the result code of an ordered common event synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-getCodeSync(): int--><!--Device-CommonEventSubscriber-getCodeSync(): int-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| number | Result code of an ordered common event. |

**Examples**

```TypeScript
let code: number = subscriber.getCodeSync();
console.info(`Succeeded in getting code, code is ${JSON.stringify(code)}`);
```

## getData

```TypeScript
getData(callback: AsyncCallback<string>): void
```

Obtains the result code of an ordered common event. This API uses an asynchronous callback to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-getData(callback: AsyncCallback<string>): void--><!--Device-CommonEventSubscriber-getData(callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the result data of an ordered common event is successfully obtained, **err** is **undefined**, and **data** is the data obtained; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
// Obtain the result data of an ordered common event.
subscriber.getData((err: BusinessError, data: string) => {
  if (err) {
    console.error(`Failed to get data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting data, data is ${JSON.stringify(data)}`);
});
```

## getData

```TypeScript
getData(): Promise<string>
```

Obtains the result code of an ordered common event. This API uses a promise to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-getData(): Promise<string>--><!--Device-CommonEventSubscriber-getData(): Promise<string>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result code of an ordered common event. |

**Examples**

```TypeScript
subscriber.getData().then((data: string) => {
  console.info(`Succeeded in getting data, data is ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get data. Code is ${err.code}, message is ${err.message}`);
});
```

## getDataSync

```TypeScript
getDataSync(): string
```

Obtains the result code of an ordered common event synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-getDataSync(): string--><!--Device-CommonEventSubscriber-getDataSync(): string-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| string | Result code of an ordered common event. |

**Examples**

```TypeScript
let data: string = subscriber.getDataSync();
console.info(`Succeeded in getting data, data is ${data}`);
```

## getSubscribeInfo

```TypeScript
getSubscribeInfo(callback: AsyncCallback<CommonEventSubscribeInfo>): void
```

Obtains the subscriber information. This API uses an asynchronous callback to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-getSubscribeInfo(callback: AsyncCallback<CommonEventSubscribeInfo>): void--><!--Device-CommonEventSubscriber-getSubscribeInfo(callback: AsyncCallback<CommonEventSubscribeInfo>): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[CommonEventSubscribeInfo](arkts-basicservices-commoneventsubscribeinfo-i.md)&gt; | Yes | Callback used to return the result. If the subscriber information is successfully obtained, **err** is **undefined** and **data** is the subscription information of the subscriber. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.getSubscribeInfo((err: BusinessError, subscribeInfo: commonEventManager.CommonEventSubscribeInfo) => {
  if (err) {
    console.error(`Failed to get subscribe info. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo)}`);
});
```

## getSubscribeInfo

```TypeScript
getSubscribeInfo(): Promise<CommonEventSubscribeInfo>
```

Obtains the subscriber information. This API uses a promise to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-getSubscribeInfo(): Promise<CommonEventSubscribeInfo>--><!--Device-CommonEventSubscriber-getSubscribeInfo(): Promise<CommonEventSubscribeInfo>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CommonEventSubscribeInfo](arkts-basicservices-commoneventsubscribeinfo-i.md)&gt; | Promise used to return the result. |

**Examples**

```TypeScript
subscriber.getSubscribeInfo().then((subscribeInfo: commonEventManager.CommonEventSubscribeInfo) => {
  console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get subscribe info. Code is ${err.code}, message is ${err.message}`);
});
```

## getSubscribeInfoSync

```TypeScript
getSubscribeInfoSync(): CommonEventSubscribeInfo
```

Obtains the subscriber information synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-getSubscribeInfoSync(): CommonEventSubscribeInfo--><!--Device-CommonEventSubscriber-getSubscribeInfoSync(): CommonEventSubscribeInfo-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| [CommonEventSubscribeInfo](arkts-basicservices-commoneventsubscribeinfo-i.md) | Subscriber information. |

**Examples**

```TypeScript
let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = subscriber.getSubscribeInfoSync();
console.info(`Succeeded in getting subscribe info, subscribe info is ${JSON.stringify(subscribeInfo)}`);
```

## isOrderedCommonEvent

```TypeScript
isOrderedCommonEvent(callback: AsyncCallback<boolean>): void
```

Checks whether the current common event is an ordered common event. This API uses an asynchronous callback to return the result.

**Since:** 7

<!--Device-CommonEventSubscriber-isOrderedCommonEvent(callback: AsyncCallback<boolean>): void--><!--Device-CommonEventSubscriber-isOrderedCommonEvent(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the query is successful, **err** is **undefined**. If **data** is **true**, the common event is ordered; if **data** is **false**, the common event is not ordered. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.isOrderedCommonEvent((err: BusinessError, isOrdered: boolean) => {
  if (err) {
    console.error(`Failed to check ordered common event. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`isOrderedCommonEvent ${JSON.stringify(isOrdered)}`);
});
```

## isOrderedCommonEvent

```TypeScript
isOrderedCommonEvent(): Promise<boolean>
```

Checks whether the current common event is an ordered common event. This API uses a promise to return the result.

**Since:** 7

<!--Device-CommonEventSubscriber-isOrderedCommonEvent(): Promise<boolean>--><!--Device-CommonEventSubscriber-isOrderedCommonEvent(): Promise<boolean>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates an ordered common event, and the value **false** indicates an [unordered common event](../../../basic-services/common-event/common-event-glossary.md#unordered-common-event). |

**Examples**

```TypeScript
subscriber.isOrderedCommonEvent().then((isOrdered: boolean) => {
  console.info(`isOrderedCommonEvent ${JSON.stringify(isOrdered)}`);
}).catch((err: BusinessError) => {
  console.error(`isOrderedCommonEvent failed, code is ${err.code}, message is ${err.message}`);
});
```

## isOrderedCommonEventSync

```TypeScript
isOrderedCommonEventSync(): boolean
```

Checks whether the current common event is an ordered common event synchronously.

**Since:** 10

<!--Device-CommonEventSubscriber-isOrderedCommonEventSync(): boolean--><!--Device-CommonEventSubscriber-isOrderedCommonEventSync(): boolean-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the common event is an ordered one; returns **false** if the common event is an unordered one. |

**Examples**

```TypeScript
let isOrdered: boolean = subscriber.isOrderedCommonEventSync();
console.info(`isOrderedCommonEventSync ${JSON.stringify(isOrdered)}`);
```

## isStickyCommonEvent

```TypeScript
isStickyCommonEvent(callback: AsyncCallback<boolean>): void
```

Checks whether the current common event is a sticky common event. This API uses an asynchronous callback to return the result.

**Since:** 7

<!--Device-CommonEventSubscriber-isStickyCommonEvent(callback: AsyncCallback<boolean>): void--><!--Device-CommonEventSubscriber-isStickyCommonEvent(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the query is successful, **err** is **undefined**. If **data** is **true**, the common event is sticky; if **data** is **false**, the common event is not sticky. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.isStickyCommonEvent((err: BusinessError, isSticky: boolean) => {
  if (err) {
    console.error(`isStickyCommonEvent failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`isStickyCommonEvent ${JSON.stringify(isSticky)}`);
});
```

## isStickyCommonEvent

```TypeScript
isStickyCommonEvent(): Promise<boolean>
```

Checks whether the current common event is a sticky common event. This API uses a promise to return the result.

**Since:** 7

<!--Device-CommonEventSubscriber-isStickyCommonEvent(): Promise<boolean>--><!--Device-CommonEventSubscriber-isStickyCommonEvent(): Promise<boolean>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. Returns **true** if the common event is a sticky one; returns **false** otherwise. |

**Examples**

```TypeScript
subscriber.isStickyCommonEvent().then((isSticky: boolean) => {
  console.info(`isStickyCommonEvent ${JSON.stringify(isSticky)}`);
}).catch((err: BusinessError) => {
  console.error(`isStickyCommonEvent failed, code is ${err.code}, message is ${err.message}`);
});
```

## isStickyCommonEventSync

```TypeScript
isStickyCommonEventSync(): boolean
```

Checks whether the current common event is a sticky common event synchronously.

**Since:** 10

<!--Device-CommonEventSubscriber-isStickyCommonEventSync(): boolean--><!--Device-CommonEventSubscriber-isStickyCommonEventSync(): boolean-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the common event is a sticky one; returns **false** otherwise. |

**Examples**

```TypeScript
let isSticky: boolean = subscriber.isStickyCommonEventSync();
console.info(`isStickyCommonEventSync ${JSON.stringify(isSticky)}`);
```

## setCode

```TypeScript
setCode(code: number, callback: AsyncCallback<void>): void
```

Sets the result code and data of an ordered common event. This API uses an asynchronous callback to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-setCode(code: int, callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-setCode(code: int, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Result code of an ordered common event. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.setCode(1, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set code. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting code.`);
});
```

## setCode

```TypeScript
setCode(code: number): Promise<void>
```

Sets the result code and data of an ordered common event. This API uses a promise to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-setCode(code: int): Promise<void>--><!--Device-CommonEventSubscriber-setCode(code: int): Promise<void>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Result code of an ordered common event. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.setCode(1).then(() => {
  console.info(`Succeeded in setting code.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set code. Code is ${err.code}, message is ${err.message}`);
});
```

## setCodeAndData

```TypeScript
setCodeAndData(code: number, data: string, callback: AsyncCallback<void>): void
```

Sets the result code and data of an ordered common event. This API uses an asynchronous callback to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-setCodeAndData(code: int, data: string, callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-setCodeAndData(code: int, data: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Result code of an ordered common event. |
| data | string | Yes | Result data of an ordered common event. The value is a string containing a maximum of 65,536 characters. If the length exceeds the limit, the API setting becomes invalid. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.setCodeAndData(1, 'publish_data_changed', (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set code and data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting code and data.`);
});
```

## setCodeAndData

```TypeScript
setCodeAndData(code: number, data: string): Promise<void>
```

Sets the result code and data of an ordered common event. This API uses a promise to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-setCodeAndData(code: int, data: string): Promise<void>--><!--Device-CommonEventSubscriber-setCodeAndData(code: int, data: string): Promise<void>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Result code of an ordered common event. |
| data | string | Yes | Result data of an ordered common event. The value is a string containing a maximum of 65,536 characters. If the length exceeds the limit, the API setting becomes invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.setCodeAndData(1, 'publish_data_changed').then(() => {
  console.info(`Succeeded in setting code and data.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set code and data. Code is ${err.code}, message is ${err.message}`);
});
```

## setCodeAndDataSync

```TypeScript
setCodeAndDataSync(code: number, data: string): void
```

Sets the result code of an ordered common event synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-setCodeAndDataSync(code: int, data: string): void--><!--Device-CommonEventSubscriber-setCodeAndDataSync(code: int, data: string): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Result code of an ordered common event. |
| data | string | Yes | Result data of an ordered common event. The value is a string containing a maximum of 65,536 characters. If the length exceeds the limit, the API setting becomes invalid. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
try {
  subscriber.setCodeAndDataSync(1, 'publish_data_changed');
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set code and data. Code is ${err.code}, message is ${err.message}`);
}
```

## setCodeSync

```TypeScript
setCodeSync(code: number): void
```

Sets the result code of an ordered common event synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-setCodeSync(code: int): void--><!--Device-CommonEventSubscriber-setCodeSync(code: int): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Result code of an ordered common event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
try {
  subscriber.setCodeSync(1);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set code. Code is ${err.code}, message is ${err.message}`);
}
```

## setData

```TypeScript
setData(data: string, callback: AsyncCallback<void>): void
```

Sets the result code and data of an ordered common event. This API uses an asynchronous callback to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-setData(data: string, callback: AsyncCallback<void>): void--><!--Device-CommonEventSubscriber-setData(data: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes | Result data of an ordered common event. The value is a string containing a maximum of 65,536 characters. If the length exceeds the limit, the API setting becomes invalid. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.setData('publish_data_changed', (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set data. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in setting data.`);
});
```

## setData

```TypeScript
setData(data: string): Promise<void>
```

Sets the result code and data of an ordered common event. This API uses a promise to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-setData(data: string): Promise<void>--><!--Device-CommonEventSubscriber-setData(data: string): Promise<void>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes | Result data of an ordered common event. The value is a string containing a maximum of 65,536 characters. If the length exceeds the limit, the API setting becomes invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
subscriber.setData('publish_data_changed').then(() => {
  console.info(`Succeeded in setting data.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set data. Code is ${err.code}, message is ${err.message}`);
});
```

## setDataSync

```TypeScript
setDataSync(data: string): void
```

Sets the result code of an ordered common event synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscriber-setDataSync(data: string): void--><!--Device-CommonEventSubscriber-setDataSync(data: string): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes | Result data of an ordered common event. The value is a string containing a maximum of 65,536 characters. If the length exceeds the limit, the API setting becomes invalid. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;         2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
try {
  subscriber.setDataSync('publish_data_changed');
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set data. Code is ${err.code}, message is ${err.message}`);
}
```
