# unsubscribe

## Modules to Import

```TypeScript
```

## unsubscribe

```TypeScript
function unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback<void>): void
```

Unsubscribes from common events. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [unsubscribe](arkts-basicservices-commoneventmanager-unsubscribe-f.md)

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscriber | [CommonEventSubscriber](arkts-basicservices-commoneventsubscriber-commoneventsubscriber-i.md) | Yes | Subscriber object. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | No | Callback used to return the result. |

**Examples**

```TypeScript
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

let subscriber:CommonEventManager.CommonEventSubscriber;    // Used to save the created subscriber object for subsequent subscription and unsubscription.

// Subscriber information.
let subscribeInfo:CommonEventManager.CommonEventSubscribeInfo = {
    events: ["event"]
};

// Callback for common event subscription.
let subscribeCallBack = (err:Base.BusinessError, data:CommonEventManager.CommonEventData) => {
    if (err.code) {
        console.error(`subscribe failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("subscribe " + JSON.stringify(data));
    }
}

// Callback for subscriber creation.
let createCallBack = (err:Base.BusinessError, commonEventSubscriber:CommonEventManager.CommonEventSubscriber) => {
    if (err.code) {
        console.error(`createSubscriber failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("createSubscriber");
        subscriber = commonEventSubscriber;
         // Subscribe to a common event.
        commonEvent.subscribe(subscriber, subscribeCallBack);
    }
}

// Callback for common event unsubscription.
let unsubscribeCallback = (err: Base.BusinessError) => {
    if (err.code) {
        console.error(`unsubscribe failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("unsubscribe");
    }
}

// Create a subscriber.
commonEvent.createSubscriber(subscribeInfo, createCallBack);

// Unsubscribe from the common event.
// Note: This API must be called after the subscriber is successfully created (that is, after the createCallBack callback is executed). Only the API usage is displayed here.
commonEvent.unsubscribe(subscriber, unsubscribeCallback);
```
