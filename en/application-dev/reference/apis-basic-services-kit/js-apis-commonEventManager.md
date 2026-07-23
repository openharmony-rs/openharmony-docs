# @ohos.commonEventManager (Common Event)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

This module provides APIs to publish, subscribe to, and unsubscribe from common events. This module provides a system-level event notification mechanism that allows an app to send notifications to other apps that have subscribed to the event when the system status changes (such as power-on completion, battery level change, and screen on/off) or a custom service event occurs. This mechanism enables transferring information across components and apps.

The key concepts involved in this module are as follows:
- Unordered common events: common events that CES forwards regardless of whether subscribers receive the events and when they subscribe to the events.
- Ordered common events: common events that CES forwards based on the subscriber priority. CES preferentially forwards an ordered common event to the subscriber with higher priority, waits until the subscriber receives the event, and then forwards the events to the subscriber with lower priority. Subscribers with the same priority receive common events in a random order.
- Sticky common events: common events that can be sent to a subscriber before or after they initiate a subscription. Only system apps or services can send sticky common events.

**APIs used in combination**

The event communication of this module invovles three processes: subscription, publishing, and ordered event. The subscription process and publishing process are associated through the event name. The publisher and subscriber do not need to be aware of each other.

**Subscription process: Create a subscriber, subscribe to an event, receive the event, and cancel the subscription.**

1. Configure the subscriber information, declare the name of the event to be subscribed to, and set the subscription priority, publisher permission, and package name as required.
2. Create a subscriber object using **commonEventManager.createSubscriberSync**.
3. Subscribe to an event using **commonEventManager.subscribe**. When an event is published, use a callback to receive **CommonEventData**, and process the event data in the callback.
4. Unsubscribe from the event using **commonEventManager.unsubscribe** when it is no longer needed.

**Publishing process: Publish an event (carrying data and attributes as required).**

1. Simple publishing: Publish an event by specifying only the event name using **commonEventManager.publish**.
2. Publishing with data and attributes: Configure attributes such as code, data, parameters, and **isOrdered** using **CommonEventPublishData**, and then call **publish** to publish the event.

**Ordered event process: Deliver the event by priority by collaborating with the subscriber.**

1. Set **isOrdered** to **true** using **CommonEventPublishData** and call **publish** to publish ordered events. Events are delivered in sequence based on the subscriber priority.
2. The subscriber with a higher priority receives the event first, who can modify the code and data in the callback using methods such as **setCodeAndData** for subsequent subscribers to receive.
3. After the processing is complete, call **finishCommonEvent** to deliver the event to the subscriber with the next highest priority. To stop delivering the event, call **abortCommonEvent** to mark the event as aborted.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { commonEventManager } from '@kit.BasicServicesKit';
```

## Support

System common events refer to events released by system services or system apps. Subscribing to these common events requires specific permissions and event values. For details, see [System Common Events](./common_event/commonEventManager-definitions.md).

## commonEventManager.publish

publish(event: string, callback: AsyncCallback\<void>): void

Publishes a common event. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name    | Type                | Mandatory| Description                  |
| -------- | -------------------- | ---- | ---------------------- |
| event    | string               | Yes  | Name of the common event to publish. For details, see [System Common Events](./common_event/commonEventManager-definitions.md).|
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the common event is successfully published, **err** is **undefined**; if the event fails to be published, **err** is an error object.|

**Error codes**

For details about the error codes, see [Common Event Error Codes](./errorcode-CommonEventService.md).

| ID| Error Message                           |
| -------- | ----------------------------------- | 
| 1500003  | The common event sending frequency too high.<br> Applicable versions: 20+|
| 1500007  | Failed to send the message to the common event service. |
| 1500008  | Failed to initialize the common event service. |
| 1500009  | Failed to obtain system parameters.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Publish a common event.
try {
  commonEventManager.publish('event', (err: BusinessError) => {
    if (err) {
      console.error(`Failed to publish common event. Code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info(`Succeeded in publishing common event.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to publish common event. Code is ${err.code}, message is ${err.message}`);
}
```

## commonEventManager.publish

publish(event: string, options: CommonEventPublishData, callback: AsyncCallback\<void>): void

Publishes a common event. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name    | Type                  | Mandatory| Description                  |
| -------- | ---------------------- | ---- | ---------------------- |
| event    | string                 | Yes  | Name of the common event to publish. For details, see [System Common Events](./common_event/commonEventManager-definitions.md). |
| options  | [CommonEventPublishData](./js-apis-inner-commonEvent-commonEventPublishData.md) | Yes  | Properties of the common event to publish.|
| callback | AsyncCallback\<void>   | Yes  | Callback used to return the result. If the common event is successfully published, **err** is **undefined**; if the event fails to be published, **err** is an error object. |

**Error codes**

For details about the error codes, see [Common Event Error Codes](./errorcode-CommonEventService.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 1500003  | The common event sending frequency too high.<br> Applicable versions: 20+|
| 1500007  | Failed to send the message to the common event service. |
| 1500008  | Failed to initialize the common event service. |
| 1500009  | Failed to obtain system parameters.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Common event information. The following uses an ordered common event as an example.
let options: commonEventManager.CommonEventPublishData = {
  code: 0,
  data: 'initial data',
  isOrdered: true // The common event is an ordered one.
};

// Publish a common event.
try {
  commonEventManager.publish('event', options, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to publish common event. Code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info(`Succeeded in publishing common event.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to publish common event. Code is ${err.code}, message is ${err.message}`);
}
```

## commonEventManager.createSubscriber

createSubscriber(subscribeInfo: CommonEventSubscribeInfo, callback: AsyncCallback\<CommonEventSubscriber>): void

Creates a subscriber. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name         | Type                                                        | Mandatory| Description                      |
| ------------- | ------------------------------------------------------------ | ---- | -------------------------- |
| subscribeInfo | [CommonEventSubscribeInfo](./js-apis-inner-commonEvent-commonEventSubscribeInfo.md)        | Yes  | Subscriber information.            |
| callback      | AsyncCallback\<[CommonEventSubscriber](./js-apis-inner-commonEvent-commonEventSubscriber.md#commoneventsubscriber-1)> | Yes  | Callback used to receive the created subscriber object. When a common event subscriber is successfully created, **err** is **undefined** and **data** is the **CommonEventSubscriber** object created. If the subscriber fails to be created, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.    | 

**Example**

```ts
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

## commonEventManager.createSubscriber

createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise\<CommonEventSubscriber>

Creates a subscriber. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name         | Type                                                 | Mandatory| Description          |
| ------------- | ----------------------------------------------------- | ---- | -------------- |
| subscribeInfo | [CommonEventSubscribeInfo](./js-apis-inner-commonEvent-commonEventSubscribeInfo.md) | Yes  | Subscriber information.|

**Return value**
| Type                                                     | Description            |
| --------------------------------------------------------- | ---------------- |
| Promise\<[CommonEventSubscriber](./js-apis-inner-commonEvent-commonEventSubscriber.md#commoneventsubscriber-1)> | Promise used to return the created subscriber object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.      | 

**Example**

```ts
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

## commonEventManager.createSubscriberSync<sup>10+</sup>

createSubscriberSync(subscribeInfo: CommonEventSubscribeInfo): CommonEventSubscriber

Creates a subscriber synchronously.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name         | Type                                                 | Mandatory| Description          |
| ------------- | ----------------------------------------------------- | ---- | -------------- |
| subscribeInfo | [CommonEventSubscribeInfo](./js-apis-inner-commonEvent-commonEventSubscribeInfo.md) | Yes  | Subscriber information.|

**Return value**
| Type                                                     | Description            |
| --------------------------------------------------------- | ---------------- |
| [CommonEventSubscriber](./js-apis-inner-commonEvent-commonEventSubscriber.md#commoneventsubscriber-1) | Promise used to return the subscriber object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.      | 

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Define a subscriber to save the created subscriber object for subsequent subscription and unsubscription.
let subscriber: commonEventManager.CommonEventSubscriber | null = null;
// Subscriber information.
let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
  events: ['event']
};
// Create a subscriber.
try {
  subscriber = commonEventManager.createSubscriberSync(subscribeInfo);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
}
```

## commonEventManager.subscribe

subscribe(subscriber: CommonEventSubscriber, callback: AsyncCallback\<CommonEventData>): void

Subscribes to a common event. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name      | Type                                               | Mandatory| Description                            |
| ---------- | ---------------------------------------------------- | ---- | -------------------------------- |
| subscriber | [CommonEventSubscriber](./js-apis-inner-commonEvent-commonEventSubscriber.md#commoneventsubscriber-1)     | Yes  | Subscriber object.                |
| callback   | AsyncCallback\<[CommonEventData](./js-apis-inner-commonEvent-commonEventData.md)> | Yes  | Callback used to return the result. When a common event is successfully subscribed to, the common event data is returned by **data** when the event is triggered. If the subscription fails, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Common Event Error Codes](./errorcode-CommonEventService.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 801  | Capability not supported.               |
| 1500007  | Failed to send the message to the common event service. |
| 1500008  | Failed to initialize the common event service. |
| 1500010  | The count of subscriber exceeds system specification. <br> Applicable versions: 20+|

**Example**

```ts
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
        // Subscribe to a common event.
        try {
          commonEventManager.subscribe(subscriber, (err: BusinessError, data: commonEventManager.CommonEventData) => {
            if (err) {
              console.error(`Failed to subscribe. Code is ${err.code}, message is ${err.message}`);
              return;
            }
            console.info(`Succeeded in subscribing, data is ${JSON.stringify(data)}`);
          });
        } catch (error) {
          let err: BusinessError = error as BusinessError;
          console.error(`Failed to subscribe. Code is ${err.code}, message is ${err.message}`);
        }
        return;
      }
      console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
}
```

## commonEventManager.unsubscribe

unsubscribe(subscriber: CommonEventSubscriber, callback?: AsyncCallback\<void>): void

Unsubscribes from a common event. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name      | Type                                            | Mandatory| Description                    |
| ---------- | ----------------------------------------------- | ---- | ------------------------ |
| subscriber | [CommonEventSubscriber](./js-apis-inner-commonEvent-commonEventSubscriber.md#commoneventsubscriber-1) | Yes  | Subscriber object.        |
| callback   | AsyncCallback\<void>                            | No  | Callback used to return the result. If the common event is successfully unsubscribed from, **err** is **undefined**; if the unsubscription fails, **err** is an error object. If this parameter is not passed, the subscription is canceled by default and no result is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Common Event Error Codes](./errorcode-CommonEventService.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.      | 
| 801  | Capability not supported.               |
| 1500007  | Failed to send the message to the common event service. |
| 1500008  | Failed to initialize the common event service. |

**Example**

```ts
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
        // Subscribe to a common event.
        try {
          commonEventManager.subscribe(subscriber, (err: BusinessError, data: commonEventManager.CommonEventData) => {
            if (err) {
              console.error(`Failed to subscribe. Code is ${err.code}, message is ${err.message}`);
              return;
            }
            console.info(`Succeeded in subscribing, data is ${JSON.stringify(data)}`);
          });
        } catch (error) {
          let err: BusinessError = error as BusinessError;
          console.error(`Failed to subscribe. Code is ${err.code}, message is ${err.message}`);
        }
        return;
      }
      console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
}

// Unsubscribe from the common event.
// Wait until execution of the asynchronous API subscribe is completed. Add setTimeout when necessary.
setTimeout(() => {
  try {
    commonEventManager.unsubscribe(subscriber, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to unsubscribe. Code is ${err.code}, message is ${err.message}`);
        return;
      }
      // If the subscriber is no longer used, set it to null to avoid memory leakage.
      subscriber = null;
      console.info(`Succeeded in unsubscribing.`);
    });
  } catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`Failed to unsubscribe. Code is ${err.code}, message is ${err.message}`);
  }
}, 500);
```

## commonEventManager.subscribeToEvent<sup>20+</sup>

subscribeToEvent(subscriber: CommonEventSubscriber, callback: Callback\<CommonEventData>): Promise\<void>

Subscribes to a common event. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Parameters**

| Name      | Type                                               | Mandatory| Description                            |
| ---------- | ---------------------------------------------------- | ---- | -------------------------------- |
| subscriber | [CommonEventSubscriber](./js-apis-inner-commonEvent-commonEventSubscriber.md#commoneventsubscriber-1)     | Yes  | Subscriber object.                |
| callback   | Callback\<[CommonEventData](./js-apis-inner-commonEvent-commonEventData.md)> | Yes  | Callback to be invoked when a common event is subscribed to.|

**Return value**
| Type                                                     | Description            |
| --------------------------------------------------------- | ---------------- |
| Promise\<void>   | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Common Event Error Codes](./errorcode-CommonEventService.md).

| ID| Error Message                           | 
| -------- | ----------------------------------- |
| 801  | Capability not supported.               |
| 1500007  | Failed to send the message to the common event service. |
| 1500008  | Failed to initialize the common event service. |
| 1500010  | The count of subscriber exceeds system specification. |

**Example**

```ts
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
      if (err) {
        console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
      } else {
        console.info(`Succeeded in creating subscriber.`);
        subscriber = commonEventSubscriber;
        // Subscribe to a common event.
        try {
          commonEventManager.subscribeToEvent(subscriber, (data: commonEventManager.CommonEventData) => {
            console.info(`Succeeded to receive common event, data is ${JSON.stringify(data)}`);
          }).then(() => {
            console.info(`Succeeded in subscribing.`);
          }).catch((err: BusinessError) => {
            console.error(`Failed to subscribe. Code is ${err.code}, message is ${err.message}`);
          });
        } catch (error) {
          let err: BusinessError = error as BusinessError;
          console.error(`Failed to subscribe. Code is ${err.code}, message is ${err.message}`);
        }
      }
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
}
```

## CommonEventData<sup>10+</sup>

type CommonEventData = _CommonEventData

Describes the data of a common event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

| Type| Description|
| --- | --- |
| [_CommonEventData](js-apis-inner-commonEvent-commonEventData.md) | Data of a common event.|

## CommonEventSubscriber<sup>10+</sup>

type CommonEventSubscriber = _CommonEventSubscriber

Describes the subscriber of a common event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

| Type| Description|
| --- | --- |
| [_CommonEventSubscriber](js-apis-inner-commonEvent-commonEventSubscriber.md#commoneventsubscriber-1) | Subscriber of a common event.|

## CommonEventSubscribeInfo<sup>10+</sup>

type CommonEventSubscribeInfo = _CommonEventSubscribeInfo

Describes information about a common event subscriber.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

| Type| Description|
| --- | --- |
| [_CommonEventSubscribeInfo](js-apis-inner-commonEvent-commonEventSubscribeInfo.md) | Information about a subscriber.|

## CommonEventPublishData<sup>10+</sup>

type CommonEventPublishData = _CommonEventPublishData

Describes the content and properties of a common event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.CommonEvent

| Type| Description|
| --- | --- |
| [_CommonEventPublishData](js-apis-inner-commonEvent-commonEventPublishData.md) | Content and properties of a common event.|