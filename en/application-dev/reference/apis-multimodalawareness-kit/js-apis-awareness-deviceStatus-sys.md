# @ohos.multimodalAwareness.deviceStatus (Device Status Awareness) (System API)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=9f16ca7f99d3e5febd92bb4bfa5d189019262593 translatedAt=2026-11-03T05:58:00.018Z pushedAt=2026-11-03T12:08:25.577Z nl=1 -->

This module provides the device status awareness capability. By listening for device sensor data, it provides applications with awareness capabilities such as device posture.

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.

## Modules to Import

   ```ts
   import { deviceStatus } from '@kit.MultimodalAwarenessKit';
   ```

## DeviceRotationRadian

Three-dimensional rotation status information of the device.

**System capability**: SystemCapability.MultimodalAwareness.DeviceStatus

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
| ------ | ------- | ------- | ----- | -------------- |
|  x  | number |  No  |  No  | Rotation radians of the device in the X-axis direction. |
|  y  | number |  No  |  No  | Rotation radians of the device in the Y-axis direction. |
|  z  | number |  No  |  No  | Rotation radians of the device in the Z-axis direction. |

## deviceStatus.getDeviceRotationRadian()

getDeviceRotationRadian(): Promise&lt;DeviceRotationRadian&gt;

Obtains the device posture data.

The posture data contains the rotation angles of the x, y, and z axes, that is, the Euler angles of the three axes. The definitions of the three axes are the same as those of the device sensor, and the right-handed coordinate system is used. Posture rotation angles are calculated under the z-x-y intrinsic rotation order, and derived by converting quaternions obtained via sensor fusion.

**System capability**: SystemCapability.MultimodalAwareness.DeviceStatus

**System API**: This is a system API.

**Return value**

| Type | Description |
| ----------------------------------- | ------------------ |
| Promise&lt;DeviceRotationRadian&gt; | Three-dimensional rotation status information of the device. |

**Error codes**

For details about the error codes, see [Device Status Awareness Error Codes](errorcode-deviceStatus.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Permission check failed. A non-system application uses the system API. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 32500001 | Service exception. |

**Example**

   ```ts
   import { deviceStatus } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   try {
      deviceStatus.getDeviceRotationRadian().then((radian: deviceStatus.DeviceRotationRadian) => {
         console.info('x:' + radian.x + ' y:' + radian.y + ' z:' + radian.z);
      }).catch((err: BusinessError) => {
         console.error(`Failed to get device rotation radians. Code: ${err.code}, message: ${err.message}`);
      });
   } catch (err) {
      console.error(`Failed to invoke. Code: ${err.code}, message: ${err.message}`);
   }
   ```