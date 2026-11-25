# @ohos.multimodalAwareness.deviceStatus (Device Status Awareness)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=9fddba7cff4ec815ef39c869017e0dacba49e413 translatedAt=2026-11-04T06:14:13.614Z pushedAt=2026-11-04T08:04:44.817Z nl=1 -->

This module provides the device status awareness capability. It senses the physical status of a device in real time through sensors, helping developers adjust application behavior based on the physical status of the device.

> **NOTE**
>
> The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

  ```ts
  import { deviceStatus } from '@kit.MultimodalAwarenessKit';
  ```

## SteadyStandingStatus

Defines the steady standing state (that is, stand mode).

A device enters the dock state when the device is stationary and the angle between the screen and the horizontal plane is 45 to 135 degrees. A foldable phone must be in the folded state or the fully unfolded state. The system detects the motion state and angle changes of the device through sensors to determine whether the device meets the dock state conditions.

**System capability**: SystemCapability.MultimodalAwareness.DeviceStatus

| Name               | Value  | Description                  |
| ------------------- | ---- | ---------------------- |
| STATUS_EXIT  | 0    | Exit of the stand mode.|
| STATUS_ENTER | 1    | Entry to the stand mode.|

## deviceStatus.on('steadyStandingDetect')

 on(type: 'steadyStandingDetect', callback: Callback&lt;SteadyStandingStatus&gt;): void

Subscribes to the device steady standing detection (dock state) event. It is recommended that you call off() to unsubscribe and release resources when the event is no longer needed.

**System capability**: SystemCapability.MultimodalAwareness.DeviceStatus

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | Yes   | Event type. The value is fixed at 'steadyStandingDetect', indicating device steady standing (dock state) detection. |
| callback | Callback&lt;[SteadyStandingStatus](#steadystandingstatus)&gt; | Yes   | Callback invoked to return the device steady standing (dock state) status information.                         |

**Error codes**

For details about the error codes, see [Device Status Awareness Error Codes](errorcode-deviceStatus.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 32500001 | Service exception. |
| 32500002 | Subscription failed. |

**Example**

   ```ts
   try {
      deviceStatus.on('steadyStandingDetect', (data: deviceStatus.SteadyStandingStatus) => {
         console.info(`succeeded to get status, now status = ${JSON.stringify(data)}`);
      });
   } catch (err) {
      console.error(`on failed. Code: ${err.code}, message: ${err.message}`);
   }
   ```

## deviceStatus.off('steadyStandingDetect')

off(type: 'steadyStandingDetect', callback?: Callback&lt;SteadyStandingStatus&gt;): void

Unsubscribes from the device steady standing detection (dock state) event. This API is used in scenarios where an application exits a page or no longer needs to listen for dock state changes. After the call, related resources are released.

**System capability**: SystemCapability.MultimodalAwareness.DeviceStatus

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | Required   | Event type. The value is fixed at 'steadyStandingDetect', indicating device steady standing (dock state) detection. |
| callback | Callback&lt;[SteadyStandingStatus](#steadystandingstatus)&gt; | No   | Callback for the steady standing detection event. The callback to be unsubscribed from must be the same as the one passed in during subscription. If this parameter is not specified, all callbacks currently listening for this event are unsubscribed from. |

**Error codes**

For details about the error codes, see [Device Status Awareness Error Codes](errorcode-deviceStatus.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 32500001 | Service exception. |
| 32500003 | Unsubscription failed. |

**Example**

Example 1: Unsubscribe from all callbacks of steady standing state change events.

   ```ts
   try {
      deviceStatus.off('steadyStandingDetect');
   } catch (err) {
      console.error(`off failed. Code: ${err.code}, message: ${err.message}`);
   }
   ```

Example 2: Unsubscribe from a specific callback of steady standing state change events.

   ```ts
   import { Callback } from '@kit.BasicServicesKit';

   // Define the callback variable.
   let callback : Callback<deviceStatus.SteadyStandingStatus> = (data : deviceStatus.SteadyStandingStatus) => {
      console.info('succeeded to get status, now status = ' + JSON.stringify(data));
   };
   // Subscribe to a specific callback of steady standing state change events.
   try {
      deviceStatus.on('steadyStandingDetect', callback);
   } catch (err) {
      console.error(`on failed. Code: ${err.code}, message: ${err.message}`);
   }
   // Unsubscribe from the specific callback of steady standing state change events.
   try {
      deviceStatus.off('steadyStandingDetect', callback);
   } catch (err) {
      console.error(`off failed. Code: ${err.code}, message: ${err.message}`);
   }
   ```