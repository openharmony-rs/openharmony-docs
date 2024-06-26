# Subscribing to Common Events in Dynamic Mode


## When to Use

In dynamic subscription mode, an application, when it is running, subscribes to a common event and then receives the event once it is published, together with the parameters passed in the event. For example, if an application expects to be notified of low battery so that it can reduce power consumption accordingly when running, then the application can subscribe to the low-battery event. Upon receiving the event, the application can close some unnecessary tasks to reduce power consumption. Certain system common events [require specific permissions](../../security/AccessToken/determine-application-mode.md) to subscribe to. For details, see [Required Permissions](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#support).


## Available APIs

For details about the APIs, see [API Reference](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#commoneventmanagersubscribe).

| API| Description|
| -------- | -------- |
| createSubscriber(subscribeInfo: [CommonEventSubscribeInfo](../reference/apis/js-apis-commonEventManager.md#commoneventsubscribeinfo), callback: AsyncCallback&lt;[CommonEventSubscriber](../reference/apis/js-apis-inner-commonEvent-commonEventSubscriber.md#usage)&gt;): void | Creates a subscriber. This API uses an asynchronous callback to return the result.|
| createSubscriber(subscribeInfo: CommonEventSubscribeInfo): Promise&lt;CommonEventSubscriber&gt; | Creates a subscriber. This API uses a promise to return the result.|
| subscribe(subscriber: CommonEventSubscriber, callback: AsyncCallback): void | Subscribes to common events.|


## How to Develop

1. Import the **commonEventManager** module.
   
   ```ts
   import Base from '@ohos.base';
   import commonEventManager from '@ohos.commonEventManager';
   import promptAction from '@ohos.promptAction';
   import Logger from '../utils/Logger';

   const TAG: string = 'ProcessModel';
   ```

2. Create a **subscribeInfo** object. For details about the data types and parameters of the object, see [CommonEventSubscribeInfo](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#commoneventsubscribeinfo).
   
   ```ts
   // Used to save the created subscriber object for subsequent subscription and unsubscription.
   let subscriber: commonEventManager.CommonEventSubscriber | null = null;
   // Subscriber information.
   let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
       events: ['usual.event.SCREEN_OFF'], // Subscribe to the common event screen-off.
   };
   ```

3. Create a subscriber object and save the returned object for subsequent operations such as subscription and unsubscription.
   
   ```ts
   // Callback for subscriber creation.
   commonEventManager.createSubscriber(subscribeInfo, (err: Base.BusinessError, data: commonEventManager.CommonEventSubscriber) => {
     if (err) {
       console.error(`Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
       return;
     }
     console.info('Succeeded in creating subscriber.');
     subscriber = data;
     // Callback for common event subscription.
     ...
   })
   ```

4. Create a subscription callback, which is triggered when an event is received. The data returned in the subscription callback contains information such as the common event name and data carried by the publisher. For details about the data types and parameters of the common event data, see [CommonEventData](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#commoneventdata).
   
   ```ts
   // Callback for common event subscription.
   if (this.subscriber !== null) {
     commonEventManager.subscribe(subscriber, (err: Base.BusinessError, data: commonEventManager.CommonEventData) => {
       if (err) {
         console.error(`Failed to subscribe common event. Code is ${err.code}, message is ${err.message}`);
         return;
       }
     })
   } else {
     console.error(`Need create subscriber`);
   }
   ```
 <!--no_check--> 