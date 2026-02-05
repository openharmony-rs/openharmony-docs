# Interface (AutoDeviceSwitch)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

AutoDeviceSwitch inherits from [AutoDeviceSwitchQuery](arkts-apis-camera-AutoDeviceSwitchQuery.md).

It is used to enable or disable automatic camera switching.

It is recommended that the system automatically handle input device switching, session configuration, and parameter continuity during automatic camera switching. If the system detects that the zoom ranges of the two cameras are different during camera switching, it will notify the application of the zoom range change through the **isDeviceCapabilityChanged** field in [AutoDeviceSwitchStatus](arkts-apis-camera-i.md#autodeviceswitchstatus13). However, the application still needs to handle the UX change (for example, for the zoom range adjustment, the application needs to obtain data again through the [getZoomRatioRange](arkts-apis-camera-ZoomQuery.md#getzoomratiorange11) API and update the UX). Therefore, this function is more suitable for scenarios where the UX interaction is simplified.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 13.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```

## enableAutoDeviceSwitch<sup>13+</sup>

enableAutoDeviceSwitch(enabled: boolean): void

Enables or disables automatic camera switching. You can use [isAutoDeviceSwitchSupported](arkts-apis-camera-AutoDeviceSwitchQuery.md#isautodeviceswitchsupported13) to check whether the device supports automatic camera switching.

> **NOTE**
> This API is used only for foldable devices with multiple front cameras. In different fold states, the system can automatically switch to an available front camera. It does not enable automatic switching between front and rear cameras.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Parameters**

| Name        | Type | Mandatory| Description |
| ----------- |---------------------- |---| -------------------------- |
| enabled | boolean  | Yes| Whether to enable automatic camera switching. **true** to enable, **false** otherwise.  |

**Error codes**

For details about the error codes, see [Camera Error Codes](errorcode-camera.md).

| ID  | Error Message                                                                                                                                      |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------|
| 7400101 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameters verification failed. |
| 7400102 | Operation not allowed.                                                                                                                         |
| 7400103 | Session not config.                                                                                                                            |
| 7400201 | Camera service fatal error.                                                                                                                    |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function enableAutoDeviceSwitch(session: camera.PhotoSession, isEnable: boolean): void {
  try {
    session.enableAutoDeviceSwitch(isEnable);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The enableAutoDeviceSwitch call failed, error code: ${err.code}`);
  }
}
```
