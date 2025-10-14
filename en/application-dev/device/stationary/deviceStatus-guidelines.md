# Device Status Awareness Development
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

The DeviceStatus module provides device status awareness capabilities such as obtaining the steady standing state (that is, stand mode).

For details about the APIs, see the [API Reference](../../reference/apis-multimodalawareness-kit/js-apis-awareness-deviceStatus.md).

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
| off(type: 'steadyStandingDetect', callback: Callback&lt;SteadyStandingStatus&gt;): void; | Unsubscribes from steady standing state change events. This API returns the result through a callback.                  |

### Development Procedure

1. Import the **deviceStatus** module.

   ```ts
   import { deviceStatus } from '@kit.MultimodalAwarenessKit';
   ```

2. Subscribe to steady standing state change events.

   ```ts
   try {
      deviceStatus.on('steadyStandingDetect', (data:deviceStatus.SteadyStandingStatus) => {
         console.info('succeed to get status, now status = ' + data);
      });
   } catch (err) {
      console.error('on failed, err = ' + err);
   }
   ```

3. Unsubscribe from all callbacks of steady standing state change events.

   ```ts
   try {
      deviceStatus.off('steadyStandingDetect');
   } catch (err) {
      console.error('off failed, err = ' + err);
   }
   ```

4. Unsubscribe from the specific callback of steady standing state change events.

   ```ts
   // Define the callback variable.
   let callback : Callback<deviceStatus.SteadyStandingStatus> = (data : deviceStatus. SteadyStandingStatus) => {
      console.info('succeed to get status, now status = ' + data);
   };
   // Subscribe to a specific callback of steady standing state change events.
   try {
      deviceStatus.on('steadyStandingDetect', callback);
   } catch (err) {
      console.error('on failed, err = ' + err);
   }
   // Unsubscribe from the specific callback of steady standing state change events.
   try {
      deviceStatus.off('steadyStandingDetect', callback);
   } catch (err) {
      console.error('off failed, err = ' + err);
   }
   ```
