# @ohos.multimodalAwareness.deviceStatus (Device Status Awareness)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=609b93af78bb4044c48524ed67f55f94adaac019 translatedAt=2026-09-14T01:54:38.538Z pushedAt=2026-09-14T10:03:33.573Z -->

This module provides the capability of sensing the device status. It senses the physical status of the device in real time through sensors, helping you adjust application behavior based on the physical status of the device.

> **NOTE**
>
> The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

  ```ts
  import { deviceStatus } from '@kit.MultimodalAwarenessKit';
  ```

## SteadyStandingStatus

Defines the steady standing state (that is, stand mode).

The device enters the stand mode when it is stationary and the angle between the screen and the horizontal plane is between 45 and 135 degrees. A foldable phone must be in the folded state or the fully unfolded state. The system detects the motion state and angle changes of the device through sensors to determine whether the device meets the stand mode conditions.

**System capability**: SystemCapability.MultimodalAwareness.DeviceStatus

| Name               | Value  | Description                  |
| ------------------- | ---- | ---------------------- |
| STATUS_EXIT  | 0    | Exit of the stand mode.|
| STATUS_ENTER | 1    | Entry to the stand mode.|

## deviceStatus.on('steadyStandingDetect')

 on(type: 'steadyStandingDetect', callback: Callback&lt;SteadyStandingStatus&gt;): void

Subscribes to the device steady standing state (stand mode) event. It is recommended to call **off()** to unsubscribe when it is no longer needed to release resources.

**System capability**: SystemCapability.MultimodalAwareness.DeviceStatus

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | Yes   | Event type. The value is fixed at 'steadyStandingDetect', indicating device steady standing state (stand mode) detection. |
| callback | Callback&lt;[SteadyStandingStatus](#steadystandingstatus)&gt; | Yes   | Callback invoked to return the device steady standing state (stand mode) status information.                         |

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

Unsubscribes from the device steady standing state (stand mode) event. It is used in scenarios where the application exits a page or no longer needs to listen for stand mode changes. Related resources are released after the call.

**System capability**: SystemCapability.MultimodalAwareness.DeviceStatus

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | Yes   | Event type. The value is fixed at 'steadyStandingDetect', indicating device steady standing state (stand mode) detection. |
| callback | Callback&lt;[SteadyStandingStatus](#steadystandingstatus)&gt; | No   | Callback to unregister. It must be the same as the callback passed during subscription. If this parameter is not specified, all callbacks currently listening for this event are unsubscribed. |

**Error codes**

For details about the error codes, see [Device Status Awareness Error Codes](errorcode-deviceStatus.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 32500001 | Service exception. |
| 32500003 | Unsubscription failed. |

**Examples**

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