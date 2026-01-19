# Publishing Common Events
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @michael_woo888-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

## When to Use

You can use [publish()](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#commoneventmanagerpublish) to publish a common event, which can carry data for subscribers to parse and process.

> **NOTE**
> Subscribers can receive sticky common events that have been sent. However, they must subscribe to common events of other types before receiving them. For details about subscription, see [Subscribing to Common Events](common-event-subscription.md).


## Available APIs

For details about the APIs, see [commonEventManager.publish](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#commoneventmanagerpublish).

| API                                                      | Description                    |
| ------------------------------------------------------------ | ---------------------------- |
| publish(event:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback<void\>) | Publishes a common event.              |
| publish(event:&nbsp;string,&nbsp;options:&nbsp;[CommonEventPublishData](../../reference/apis-basic-services-kit/js-apis-inner-commonEvent-commonEventPublishData.md),&nbsp;callback:&nbsp;AsyncCallback<void\>) | Publishes a common event with given properties.|


## Publishing a Common Event that Does Not Carry Information

Common events that do not carry information can be published only as unordered common events.

1. Import the related modules.
   
   <!-- @[ImportModule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/CommonEvent/entry/src/main/ets/filemanager/CreatSubscribeInfo.ets) --> 
   
   ``` TypeScript
   import { BusinessError, commonEventManager } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   
   const TAG: string = 'ProcessModel';
   const DOMAIN_NUMBER: number = 0xFF00;
   ```

2. Pass in the common event name and callback, and publish the event.
   
   <!-- @[PublicEventNoInformation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/CommonEvent/entry/src/main/ets/filemanager/CreatSubscribeInfo.ets) -->
   
   ``` TypeScript
   // Publish the common event. Replace the event field with the actual event name.
   commonEventManager.publish('event', (err: BusinessError) => {
     if (err) {
       hilog.error(DOMAIN_NUMBER, TAG,
         `Publish failed, code is ${JSON.stringify(err.code)}, message is ${JSON.stringify(err.message)}`);
     } else {
       //...
       hilog.info(DOMAIN_NUMBER, TAG, `Publish success`);
     }
   });
   ```


## Publishing a Common Event that Carries Information

Common events that carry information can be published as unordered, ordered, and sticky common events, which are specified by the **isOrdered** and **isSticky** fields of [CommonEventPublishData](../../reference/apis-basic-services-kit/js-apis-inner-commonEvent-commonEventPublishData.md).

1. Import the related modules.
   
   <!-- @[ImportModule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/CommonEvent/entry/src/main/ets/filemanager/CreatSubscribeInfo.ets) -->
   
   ``` TypeScript
   import { BusinessError, commonEventManager } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   
   const TAG: string = 'ProcessModel';
   const DOMAIN_NUMBER: number = 0xFF00;
   ```

2. Create the public event information to publish.
   
   <!-- @[PublicEventInformation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/CommonEvent/entry/src/main/ets/filemanager/CreatSubscribeInfo.ets) -->
   
   ``` TypeScript
   // Information of a common event.
   let options: commonEventManager.CommonEventPublishData = {
     code: 1, // Initial code of the common event.
     data: 'initial data', // Initial data of the common event.
   };
   ```

3. Pass in the common event name, information of the common event, and callback, and publish the event.
   
   <!-- @[PublicEventCarryingInformation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/CommonEvent/entry/src/main/ets/filemanager/CreatSubscribeInfo.ets) -->
   
   ``` TypeScript
   // Publish the common event. Replace the event field with the actual event name.
   commonEventManager.publish('event', options, (err: BusinessError) => {
     if (err) {
       hilog.error(DOMAIN_NUMBER, TAG,
         `Failed to publish common event. Code is ${err.code}, message is ${err.message}`);
     } else {
       //...
       hilog.info(DOMAIN_NUMBER, TAG, `Succeeded in publishing common event.`);
     }
   });
   ```
