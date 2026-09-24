# setStaticSubscriberState (System API)

## Modules to Import

```TypeScript
import { commonEventManager } from '@kit.BasicServicesKit';
```

## setStaticSubscriberState

```TypeScript
function setStaticSubscriberState(enable: boolean, callback: AsyncCallback<void>): void
```

Enables or disables static subscription for an app. This API uses an asynchronous callback to return the result.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether static subscription is enabled.<br> **true**: enabled; **false**: disabled. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1500007](../errorcode-CommonEventService.md#1500007-failed-to-send-a-request-through-ipc) | Failed to send the message to the common event service. |
| [1500008](../errorcode-CommonEventService.md#1500008-failed-to-initialize-the-common-event-service) | Failed to initialize the common event service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

commonEventManager.setStaticSubscriberState(true, (err: BusinessError) => {
  if (err.code != 0) {
    console.error(`setStaticSubscriberState failed, errCode: ${err.code}, errMsg: ${err.message}`);
    return;
  }
  console.info(`setStaticSubscriberState success`);
});
```


<a id="setstaticsubscriberstate-1"></a>

## setStaticSubscriberState

```TypeScript
function setStaticSubscriberState(enable: boolean): Promise<void>
```

Enables or disables static subscription for an app. This API uses a promise to return the result.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether static subscription is enabled.<br> **true**: enabled; **false**: disabled. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1500007](../errorcode-CommonEventService.md#1500007-failed-to-send-a-request-through-ipc) | Failed to send the message to the common event service. |
| [1500008](../errorcode-CommonEventService.md#1500008-failed-to-initialize-the-common-event-service) | Failed to initialize the common event service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

commonEventManager.setStaticSubscriberState(false).then(() => {
  console.info(`setStaticSubscriberState success`);
}).catch((err: BusinessError) => {
  console.error(`setStaticSubscriberState failed, errCode: ${err.code}, errMsg: ${err.message}`);
});
```


<a id="setstaticsubscriberstate-2"></a>

## setStaticSubscriberState

```TypeScript
function setStaticSubscriberState(enable: boolean, events?: Array<string>): Promise<void>
```

Enables or disables static subscription to a common event for the current app. This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether static subscription is enabled.<br> **true**: enabled; **false**: disabled. |
| events | Array&lt;string&gt; | No | List of common event names to be set. By default, the list is empty, indicating that the status of all common events subscribed to in static mode by the current app is to be set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [1500007](../errorcode-CommonEventService.md#1500007-failed-to-send-a-request-through-ipc) | Failed to send the message to the common event service. |
| [1500008](../errorcode-CommonEventService.md#1500008-failed-to-initialize-the-common-event-service) | Failed to initialize the common event service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let eventName: string[] = ['usual.event.SEND_DATA'];
commonEventManager.setStaticSubscriberState(true, eventName).then(() => {
  console.info(`setStaticSubscriberState success`);
}).catch((err: BusinessError) => {
  console.error(`setStaticSubscriberState failed, errCode: ${err.code}, errMsg: ${err.message}`);
});
```
