# @ohos.multimodalAwareness.deviceStatus (Device Status Awareness) (System API)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @saga2025-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=609b93af78bb4044c48524ed67f55f94adaac019 translatedAt=2026-09-14T01:52:41.357Z pushedAt=2026-09-14T10:03:33.571Z -->

This module provides the device status awareness capability. By listening for device sensor data, it provides applications with awareness capabilities such as device posture.

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.

## Modules to Import

   ```ts
   import { deviceStatus } from '@kit.MultimodalAwarenessKit';
   ```

## deviceStatus.getDeviceRotationRadian()

getDeviceRotationRadian(): Promise&lt;DeviceRotationRadian&gt;

Obtains the device posture data.

The posture data contains the rotation angles of the x, y, and z axes, that is, the Euler angles of the three axes. The definitions of the three axes are the same as those of the device sensor, and the right-handed coordinate system is used. Posture rotation angles are calculated under the z-x-y intrinsic rotation order, and derived by converting quaternions obtained via sensor fusion.

**System capability**: SystemCapability.MultimodalAwareness.DeviceStatus

**System API**: This is a system API.

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