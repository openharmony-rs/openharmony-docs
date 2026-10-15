# createSubscriber

## Modules to Import

```TypeScript
```

<a id="createsubscriber1"></a>

## createSubscriber

```TypeScript
function createSubscriber(
    subscribeInfo: CommonEventSubscribeInfo,
    callback: AsyncCallback<CommonEventSubscriber>
  ): void
```

Creates a subscriber. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [createSubscriber](arkts-basicservices-commoneventmanager-createsubscriber-f.md#createsubscriber1)( subscribeInfo: CommonEventSubscribeInfo, callback: AsyncCallback&lt;CommonEventSubscriber&gt; )

<!--Device-commonEvent-function createSubscriber(    subscribeInfo: CommonEventSubscribeInfo,    callback: AsyncCallback<CommonEventSubscriber>  ): void--><!--Device-commonEvent-function createSubscriber(    subscribeInfo: CommonEventSubscribeInfo,    callback: AsyncCallback<CommonEventSubscriber>  ): void-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscribeInfo | [CommonEventSubscribeInfo](arkts-basicservices-commoneventsubscribeinfo-i.md) | Yes | Subscriber information. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[CommonEventSubscriber](arkts-basicservices-commoneventsubscriber-i.md)&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

let subscriber:CommonEventManager.CommonEventSubscriber; // Used to save the created subscriber object for subsequent subscription and unsubscription.

// Subscriber information.
let subscribeInfo:CommonEventManager.CommonEventSubscribeInfo = {
    events: ["event"]
};

// Callback for subscriber creation.
let createCallBack = (err:Base.BusinessError, commonEventSubscriber:CommonEventManager.CommonEventSubscriber) => {
    if (err.code) {
        console.error(`createSubscriber failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("createSubscriber");
        subscriber = commonEventSubscriber;
    }
}

// Create a subscriber.
commonEvent.createSubscriber(subscribeInfo, createCallBack);
```


<a id="createsubscriber2"></a>

## createSubscriber

```TypeScript
function createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise<CommonEventSubscriber>
```

Creates a subscriber. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [createSubscriber](arkts-basicservices-commoneventmanager-createsubscriber-f.md#createsubscriber2)(subscribeInfo: CommonEventSubscribeInfo)

<!--Device-commonEvent-function createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise<CommonEventSubscriber>--><!--Device-commonEvent-function createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise<CommonEventSubscriber>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscribeInfo | [CommonEventSubscribeInfo](arkts-basicservices-commoneventsubscribeinfo-i.md) | Yes | Subscriber information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CommonEventSubscriber](arkts-basicservices-commoneventsubscriber-i.md)&gt; | Promise used to return the subscriber object. |

**Examples**

```TypeScript
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

let subscriber:CommonEventManager.CommonEventSubscriber; // Used to save the created subscriber object for subsequent subscription and unsubscription.

// Subscriber information.
let subscribeInfo:CommonEventManager.CommonEventSubscribeInfo = {
    events: ["event"]
};

// Create a subscriber.
commonEvent.createSubscriber(subscribeInfo).then((commonEventSubscriber:CommonEventManager.CommonEventSubscriber) => {
    console.info("createSubscriber");
    subscriber = commonEventSubscriber;
}).catch((err:Base.BusinessError) => {
    console.error(`createSubscriber failed, code is ${err.code}, message is ${err.message}`);
});
```
