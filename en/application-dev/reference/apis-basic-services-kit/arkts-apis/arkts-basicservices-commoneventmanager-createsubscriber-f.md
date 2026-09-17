# createSubscriber

## Modules to Import

```TypeScript
import { commonEventManager } from '@kit.BasicServicesKit';
```

## createSubscriber

```TypeScript
function createSubscriber(
    subscribeInfo: CommonEventSubscribeInfo,
    callback: AsyncCallback<CommonEventSubscriber>
  ): void
```

Creates a subscriber. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscribeInfo | [CommonEventSubscribeInfo](arkts-basicservices-commoneventmanager-commoneventsubscribeinfo-t.md) | Yes | Subscriber information. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[CommonEventSubscriber](arkts-basicservices-commoneventmanager-commoneventsubscriber-t.md)&gt; | Yes | Callback used to receive the created subscriber object. When a common event subscriber is successfully created, **err** is **undefined** and **data** is the **CommonEventSubscriber** object created. If the subscriber fails to be created, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Define a subscriber to save the created subscriber object for subsequent subscription and unsubscription.
let subscriber: commonEventManager.CommonEventSubscriber | null = null;
// Subscriber information.
let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
  events: ['event']
};

// Create a subscriber.
try {
  commonEventManager.createSubscriber(subscribeInfo,
    (err: BusinessError, commonEventSubscriber: commonEventManager.CommonEventSubscriber) => {
      if (!err) {
        console.info(`Succeeded in creating subscriber.`);
        subscriber = commonEventSubscriber;
        return;
      }
      console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Define a subscriber to save the created subscriber object for subsequent subscription and unsubscription.
let subscriber: commonEventManager.CommonEventSubscriber | null = null;
// Subscriber information.
let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
  events: ['event']
};
// Create a subscriber.
commonEventManager.createSubscriber(subscribeInfo).then((commonEventSubscriber: commonEventManager.CommonEventSubscriber) => {
  console.info(`Succeeded in creating subscriber.`);
  subscriber = commonEventSubscriber;
}).catch((err: BusinessError) => {
  console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
});
```


## createSubscriber

```TypeScript
function createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise<CommonEventSubscriber>
```

Creates a subscriber. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscribeInfo | [CommonEventSubscribeInfo](arkts-basicservices-commoneventmanager-commoneventsubscribeinfo-t.md) | Yes | Subscriber information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CommonEventSubscriber](arkts-basicservices-commoneventmanager-commoneventsubscriber-t.md)&gt; | Promise used to return the created subscriber object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

See [createSubscriber](#createsubscriber)
