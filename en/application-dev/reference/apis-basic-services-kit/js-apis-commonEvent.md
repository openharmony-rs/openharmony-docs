# @ohos.commonEvent (Common Event) (Deprecated)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

The **CommonEvent** module provides capabilities to publish, subscribe to, and unsubscribe from common events, as well as obtain and modify the common event result code and result data.

> **NOTE**
>
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [@ohos.commonEventManager](js-apis-commonEventManager.md) instead.

## Modules to Import

```ts
import commonEvent from '@ohos.commonEvent';
```

## Support

A system common event is an event that is published by a system service or system application and requires specific permissions to subscribe to. To publish or subscribe to this type of event, you must follow the event-specific definitions.

For details about the definitions of all system common events, see [System Common Events](./common_event/commonEvent-definitions.md).

## commonEvent.publish<sup>(deprecated)</sup>

publish(event: string, callback: AsyncCallback\<void>): void

Publishes a common event with given properties. This API uses an asynchronous callback to return the result.

> **NOTE**
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [commonEventManager.publish](js-apis-commonEventManager.md#commoneventmanagerpublish) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name    | Type                | Mandatory| Description                  |
| -------- | -------------------- | ---- | ---------------------- |
| event    | string               | Yes  | Name of the common event to publish.|
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result of publishing a common event.|

**Example**

```ts
import Base from '@ohos.base';

// Callback for common event publication.
let publishCallBack = (err: Base.BusinessError) => {
    if (err.code) {
        console.error(`publish failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info('publish');
    }
}

// Publish a common event.
commonEvent.publish("event", publishCallBack);
```

## commonEvent.publish<sup>(deprecated)</sup>

publish(event: string, options: CommonEventPublishData, callback: AsyncCallback\<void>): void

Publishes a common event with given properties. This API uses an asynchronous callback to return the result.

> **NOTE**
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [commonEventManager.publish](js-apis-commonEventManager.md#commoneventmanagerpublish-1) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name    | Type                  | Mandatory| Description                  |
| -------- | ---------------------- | ---- | ---------------------- |
| event    | string                 | Yes  | Name of the common event to publish. |
| options  | [CommonEventPublishData](./js-apis-inner-commonEvent-commonEventPublishData.md) | Yes  | Properties of the common event to publish.|
| callback | AsyncCallback\<void>   | Yes  | Callback used to return the result of publishing a common event. |

**Example**


```ts
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

// Information of a common event.
let options:CommonEventManager.CommonEventPublishData = {
    code: 0,             // Initial code of the common event.
    data: "initial data", // Initial data of the common event.
    isOrdered: true  // The common event is an ordered one.
};

// Callback for common event publication.
let publishCallBack = (err: Base.BusinessError) => {
    if (err.code) {
        console.error(`publish failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("publish");
    }
}

// Publish a common event.
commonEvent.publish("event", options, publishCallBack);
```

## commonEvent.createSubscriber<sup>(deprecated)</sup>

createSubscriber(subscribeInfo: CommonEventSubscribeInfo, callback: AsyncCallback\<CommonEventSubscriber>): void

Creates a subscriber. This API uses an asynchronous callback to return the result.

> **NOTE**
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [commonEventManager.createSubscriber](js-apis-commonEventManager.md#commoneventmanagercreatesubscriber) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name         | Type                                                        | Mandatory| Description                      |
| ------------- | ------------------------------------------------------------ | ---- | -------------------------- |
| subscribeInfo | [CommonEventSubscribeInfo](./js-apis-inner-commonEvent-commonEventSubscribeInfo.md)        | Yes  | Subscriber information.            |
| callback      | AsyncCallback\<[CommonEventSubscriber](./js-apis-inner-commonEvent-commonEventSubscriber.md)> | Yes  | Callback used to return the result.|

**Example**


```ts
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

## commonEvent.createSubscriber<sup>(deprecated)</sup>

createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise\<CommonEventSubscriber>

Creates a subscriber. This API uses a promise to return the result.

> **NOTE**
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [commonEventManager.createSubscriber](js-apis-commonEventManager.md#commoneventmanagercreatesubscriber-1) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name         | Type                                                 | Mandatory| Description          |
| ------------- | ----------------------------------------------------- | ---- | -------------- |
| subscribeInfo | [CommonEventSubscribeInfo](./js-apis-inner-commonEvent-commonEventSubscribeInfo.md) | Yes  | Subscriber information.|

**Return value**
| Type                                                     | Description            |
| --------------------------------------------------------- | ---------------- |
| Promise\<[CommonEventSubscriber](./js-apis-inner-commonEvent-commonEventSubscriber.md)> | Promise used to return the subscriber object.|

**Example**

```ts
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

## commonEvent.subscribe<sup>(deprecated)</sup>

subscribe(subscriber: CommonEventSubscriber, callback: AsyncCallback\<CommonEventData>): void

Subscribes to common events. This API uses an asynchronous callback to return the result.

> **NOTE**
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [commonEventManager.subscribe](js-apis-commonEventManager.md#commoneventmanagersubscribe) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name      | Type                                               | Mandatory| Description                            |
| ---------- | ---------------------------------------------------- | ---- | -------------------------------- |
| subscriber | [CommonEventSubscriber](./js-apis-inner-commonEvent-commonEventSubscriber.md)     | Yes  | Subscriber object.                |
| callback   | AsyncCallback\<[CommonEventData](./js-apis-inner-commonEvent-commonEventData.md)> | Yes  | Callback to be invoked when a common event is subscribed to.|

**Example**

```ts
import Base from '@ohos.base';
import CommonEventManager from '@ohos.commonEventManager';

let subscriber:CommonEventManager.CommonEventSubscriber; // Used to save the created subscriber object for subsequent subscription and unsubscription.

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

// Create a subscriber.
commonEvent.createSubscriber(subscribeInfo, createCallBack);
```

## commonEvent.unsubscribe<sup>(deprecated)</sup>

unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback\<void>): void

Unsubscribes from common events. This API uses an asynchronous callback to return the result.

> **NOTE**
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [commonEventManager.unsubscribe](js-apis-commonEventManager.md#commoneventmanagerunsubscribe) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name      | Type                                            | Mandatory| Description                    |
| ---------- | ----------------------------------------------- | ---- | ------------------------ |
| subscriber | [CommonEventSubscriber](./js-apis-inner-commonEvent-commonEventSubscriber.md) | Yes  | Subscriber object.        |
| callback   | AsyncCallback\<void>                            | No  | Callback used to return the result.|

**Example**

```ts
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
