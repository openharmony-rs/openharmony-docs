# removeStickyCommonEvent (System API)

## Modules to Import

```TypeScript
import { commonEventManager } from '@kit.BasicServicesKit';
```

## removeStickyCommonEvent

```TypeScript
function removeStickyCommonEvent(event: string, callback: AsyncCallback<void>): void
```

Removes a sticky common event. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.COMMONEVENT_STICKY

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Sticky common event to remove. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the sticky common event is successfully removed, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1500004](../errorcode-CommonEventService.md#1500004-failed-to-send-system-common-events) | A third-party application cannot send system common events. |
| [1500007](../errorcode-CommonEventService.md#1500007-failed-to-send-a-request-through-ipc) | Failed to send the message to the common event service. |
| [1500008](../errorcode-CommonEventService.md#1500008-failed-to-initialize-the-common-event-service) | Failed to initialize the common event service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

commonEventManager.removeStickyCommonEvent('sticky_event', (err: BusinessError) => {
  if (err) {
    console.error(`removeStickyCommonEvent failed, errCode: ${err.code}, errMsg: ${err.message}`);
    return;
  }
  console.info(`removeStickyCommonEvent success`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

commonEventManager.removeStickyCommonEvent('sticky_event').then(() => {
  console.info(`removeStickyCommonEvent success`);
}).catch((err: BusinessError) => {
  console.error(`removeStickyCommonEvent failed, errCode: ${err.code}, errMsg: ${err.message}`);
});
```


## removeStickyCommonEvent

```TypeScript
function removeStickyCommonEvent(event: string): Promise<void>
```

Removes a sticky common event that has been published. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.COMMONEVENT_STICKY

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Sticky common event to remove. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1500004](../errorcode-CommonEventService.md#1500004-failed-to-send-system-common-events) | A third-party application cannot send system common events. |
| [1500007](../errorcode-CommonEventService.md#1500007-failed-to-send-a-request-through-ipc) | Failed to send the message to the common event service. |
| [1500008](../errorcode-CommonEventService.md#1500008-failed-to-initialize-the-common-event-service) | Failed to initialize the common event service. |

**Examples**

See [removeStickyCommonEvent](#removestickycommonevent)
