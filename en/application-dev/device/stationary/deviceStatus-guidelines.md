# Device Status Awareness Development

<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=1d432eccd2a4695fccf1a14b13e10c9b4f4ac00c translatedAt=2026-07-28T06:46:58.577Z pushedAt=2026-07-28T09:08:16.974Z -->

The **DeviceStatus** module provides device status awareness capabilities. It can be used to obtain device information, such as the steady standing state (stand mode).

For details about the APIs, see [@ohos.multimodalAwareness.deviceStatus (Device Status Awareness)](../../reference/apis-multimodalawareness-kit/js-apis-awareness-deviceStatus.md).

## Concepts

Understanding the following concepts would be helpful for you in device status awareness development:

- Stand mode

    A device enters stand mode when it is stationary, and its screen is at an angle between 45 and 135 degrees relative to the horizontal plane. For a foldable, it must be in a folded state or fully unfolded state.

## How to Develop

### Overview

During development, you can subscribe to steady standing state change events and obtain the current state through the callback passed in during subscription.

This function is supported since API version 18.

### Constraints

The device must support accelerometers.

### APIs

| API                                                      | Description                                  |
| ------------------------------------------------------------ | -------------------------------------- |
| on(type: 'steadyStandingDetect', callback: Callback&lt;SteadyStandingStatus&gt;): void; | Subscribes to steady standing state change events. This API returns the result through a callback.|
| off(type: 'steadyStandingDetect', callback?: Callback&lt;SteadyStandingStatus&gt;): void; | Unsubscribes from steady standing state change events. |

### Development Procedure

1. Import the required module.

   <!-- @[import_the_device_status_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/DeviceStatus/entry/src/main/ets/pages/Index.ets) --> 

   ``` TypeScript
   import { deviceStatus } from '@kit.MultimodalAwarenessKit';
   ```

2. Subscribe to steady standing state change events.

   <!-- @[device_status_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/DeviceStatus/entry/src/main/ets/pages/Index.ets) --> 

   ``` TypeScript
   try {
     deviceStatus.on('steadyStandingDetect', (data:deviceStatus.SteadyStandingStatus) => {
       console.info('succeed to get status, now status = ' + data);
     });
     // ...
   } catch (err) {
     console.error('on failed, err = ' + err);
     // ...
   }
   ```

3. Unsubscribe from all steady standing state change events subscribed by this client.

   <!-- @[device_status_unsubscribe_all](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/DeviceStatus/entry/src/main/ets/pages/Index.ets) --> 

   ``` TypeScript
   try {
     deviceStatus.off('steadyStandingDetect');
     // ...
   } catch (err) {
     console.error('off failed, err = ' + err);
     // ...
   }
   ```

4. Unsubscribe from the specific callback of steady standing state change events.

   <!-- @[device_status_unsubscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/DeviceStatus/entry/src/main/ets/pages/Index.ets) --> 

   ``` TypeScript
   // Define a callback.
   let callback : Callback<deviceStatus.SteadyStandingStatus> = (data : deviceStatus.SteadyStandingStatus) => {
     console.info('succeed to get status, now status = ' + data);
   };
   // Subscribe to steady standing state change events with the callback.
   try {
     deviceStatus.on('steadyStandingDetect', callback);
     // ...
   } catch (err) {
     console.error('on failed, err = ' + err);
     // ...
   }
   // Unsubscribes the specified callback from steady standing state change events for this client.
   try {
     deviceStatus.off('steadyStandingDetect', callback);
     // ...
   } catch (err) {
     console.error('off failed, err = ' + err);
     // ...
   }
   ```