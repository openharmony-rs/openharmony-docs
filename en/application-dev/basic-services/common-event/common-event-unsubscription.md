# Unsubscribing from Common Events in Dynamic Mode
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4faed534b39ef26ef8f9b647802a53e9f8d2b792 translatedAt=2026-11-16T04:24:26.910Z pushedAt=2026-11-16T06:31:14.023Z nl=1 -->

## When to Use

After a service is finished in the dynamic mode, the subscriber should proactively unsubscribe from the event. You can call [unsubscribe()](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#commoneventmanagerunsubscribe) to unsubscribe from a common event that is no longer required.


## Available APIs

| API| Description|
| -------- | -------- |
| [unsubscribe](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#commoneventmanagerunsubscribe)(subscriber:&nbsp;CommonEventSubscriber,&nbsp;callback?:&nbsp;AsyncCallback<void\>) | Unsubscribes from a common event.|


## How to Develop

1. Import the related modules.
   
   <!-- @[ImportModule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/CommonEvent/entry/src/main/ets/filemanager/CreatSubscribeInfo.ets) -->
   
   ``` TypeScript
   import { BusinessError, commonEventManager } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   
   const TAG: string = 'ProcessModel';
   const DOMAIN_NUMBER: number = 0xFF00;
   ```

2. Subscribe to an event by following the procedure described in [Subscribing to Common Events in Dynamic Mode](common-event-subscription.md).

3. Call [unsubscribe()](../../reference/apis-basic-services-kit/js-apis-commonEventManager.md#commoneventmanagerunsubscribe) in **CommonEvent** to unsubscribe from an event.
   
   <!-- @[UnsubscribePublicEvents](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/common_event/CommonEvent/entry/src/main/ets/filemanager/CreatSubscribeInfo.ets) -->
   
   ``` TypeScript
   // subscriberCustom is the subscriber object created when subscribing to events.
   if (subscriberCustom !== null) {
     commonEventManager.unsubscribe(subscriberCustom, (err: BusinessError) => {
       if (err) {
         hilog.error(DOMAIN_NUMBER, TAG,
           `Failed to unsubscribe. code is ${err.code}, message is ${err.message}`);
       } else {
         hilog.info(DOMAIN_NUMBER, TAG, `Succeeded in unsubscribing.`);
         subscriberCustom = null;
       }
     })
   }
   ```
