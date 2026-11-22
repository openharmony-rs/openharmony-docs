# Subscribing to Common Events in Dynamic Mode
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=1ded46b3f2c6157598c112b16f192beb1f37cf1d translatedAt=2026-11-06T12:01:04.959Z pushedAt=2026-11-09T12:21:12.229Z nl=1 -->

## When to Use

Dynamic subscription means that an application subscribes to a common event while it is running. During the running period, if a subscribed event is published, the application that subscribes to this event will receive the event and the parameters carried by it.

For example, if an application expects to be notified of low battery so that it can reduce power consumption accordingly when running, then the application can subscribe to the low-battery event. Upon receiving the event, the application can close some unnecessary tasks to reduce power consumption.

To subscribe to some system common events, you need to [apply for permissions](../../security/AccessToken/determine-application-mode.md) first. For the permissions required for subscribing to these events, see [System-Defined Common Events](../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md).

> **NOTE**
>
> The lifecycle of the subscriber object needs to be managed by the application. If the subscriber object is no longer used, [unsubscribe from it in dynamic mode](common-event-unsubscription.md) to destroy and release it. This way avoids subscription failures of other services and memory leakage when the number of intra-process subscribers exceeds 200.
> 
> The callback of common events in dynamic subscription mode is affected by the application status. When the application is in the background, the callback cannot receive common events subscribed dynamically. When the application is switched from the background to the foreground, the callback can receive common events listened for within 30 seconds before the switch.
>
> Common events between the main application and the cloned application are isolated from each other, that is, they cannot receive the common events mutually.

## Available APIs

For details about the APIs, see [@ohos.commonEventManager](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md).

| API| Description|
| -------- | -------- |
| [createSubscriber](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#commoneventmanagercreatesubscriber)(subscribeInfo:&nbsp;CommonEventSubscribeInfo,&nbsp;callback:&nbsp;AsyncCallback&lt;CommonEventSubscriber&gt;):&nbsp;void | Creates a subscriber. This API uses an asynchronous callback to return the result.|
| [createSubscriber](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#commoneventmanagercreatesubscriber-1)(subscribeInfo:&nbsp;CommonEventSubscribeInfo):&nbsp;Promise&lt;CommonEventSubscriber&gt; | Creates a subscriber. This API uses a promise to return the result.|
| [subscribe](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#commoneventmanagersubscribe)(subscriber:&nbsp;CommonEventSubscriber,&nbsp;callback:&nbsp;AsyncCallback&lt;CommonEventData&gt;):&nbsp;void | Subscribes to common events.|


## How to Develop

1. Import the related modules.
   
   <!-- @[ImportModule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/CommonEvent/entry/src/main/ets/filemanager/CreatSubscribeInfo.ets) -->
   
   ``` TypeScript
   import { BusinessError, commonEventManager } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   
   const TAG: string = 'ProcessModel';
   const DOMAIN_NUMBER: number = 0xFF00;
   ```

2. Create a **subscribeInfo** object. For details about the data types and parameters of the object, see [CommonEventSubscribeInfo](../../reference/apis-basic-services-kit/js-apis-inner-commonEvent-commonEventSubscribeInfo.md).
   - Custom common events: defined by applications.
   
     <!-- @[CreateCustomSubscriberInformation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/CommonEvent/entry/src/main/ets/filemanager/CreatSubscribeInfo.ets) -->
     
     ``` TypeScript
     // Used to save the created subscriber object for subsequent subscription and unsubscription.
     let subscriberCustom: commonEventManager.CommonEventSubscriber | null = null;
     // Subscriber information. Replace the 'event' field with the actual event name.
     let subscribeInfoCustom: commonEventManager.CommonEventSubscribeInfo = {
       events: ['event']  // Subscribe to a custom common event.
     };
     ```

   - System common events: common events defined inside CES. Currently, only system applications and system services can publish them, such as common events for HAP installation, update, and uninstallation. For the currently supported system common events, see [System-Defined Common Events](../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md).
   
     <!-- @[CreateSystemSubscriberInformation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/CommonEvent/entry/src/main/ets/filemanager/CreatSubscribeInfo.ets) -->
     
     ``` TypeScript
     // Used to save the created subscriber object for subsequent subscription and unsubscription.
     let subscriberSystem: commonEventManager.CommonEventSubscriber | null = null;
     // Subscriber information. Use the corresponding common event as required.
     let subscribeInfoSystem: commonEventManager.CommonEventSubscribeInfo = {
       events: [commonEventManager.Support.COMMON_EVENT_SCREEN_OFF]  // Subscribe to the screen-off event.
     };
     ```

3. Create a subscriber object and save the returned object for subsequent operations such as subscription, unsubscription, and event callback.
   
   <!-- @[CreateSubscriberCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/CommonEvent/entry/src/main/ets/filemanager/CreatSubscribeInfo.ets) -->
   
   ``` TypeScript
   // Callback for subscriber creation.
   commonEventManager.createSubscriber(subscribeInfoCustom,
     (err: BusinessError, data: commonEventManager.CommonEventSubscriber) => {
       if (err) {
         hilog.error(DOMAIN_NUMBER, TAG,
           `Failed to create subscriber. Code is ${err.code}, message is ${err.message}`);
         return;
       }
       hilog.info(DOMAIN_NUMBER, TAG, 'Succeeded in creating subscriber.');
       subscriberCustom = data;
     })
   ```

4. Create a subscription callback, which is triggered when an event is received. The data returned in the subscription callback contains information such as the common event name and data carried by the publisher. For details about the data types and parameters of the common event data, see [CommonEventData](../../reference/apis-basic-services-kit/js-apis-inner-commonEvent-commonEventData.md).
   
   <!-- @[SubscribeToPublicEvents](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/CommonEvent/entry/src/main/ets/filemanager/CreatSubscribeInfo.ets) -->
   
   ``` TypeScript
   // Callback for common event subscription.
   if (subscriberCustom !== null) {
     commonEventManager.subscribe(subscriberCustom,
       (err: BusinessError, data: commonEventManager.CommonEventData) => {
         if (err) {
           hilog.error(DOMAIN_NUMBER, TAG,
             `Failed to subscribe common event. Code is ${err.code}, message is ${err.message}`);
           return;
         }
         hilog.info(DOMAIN_NUMBER, TAG, `Succeeded in subscribing, data is ${JSON.stringify(data)}`);
       })
   } else {
     hilog.error(DOMAIN_NUMBER, TAG, `Need create subscriber`);
   }
   ```

<!--RP1-->
<!--RP1End-->