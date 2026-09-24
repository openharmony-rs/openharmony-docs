# AutoDeviceSwitch

```TypeScript
interface AutoDeviceSwitch extends AutoDeviceSwitchQuery
```

**AutoDeviceSwitch** inherits from [AutoDeviceSwitchQuery](arkts-camera-camera-autodeviceswitchquery-i.md) and is used to enable or disable automatic camera switch. This capability can be used only on foldable devices. For details about the development, see [Practices for Automatic Camera Switching (ArkTS)](../../../media/camera/camera-auto-switch.md).

It is recommended that the system automatically handle input device switching, session configuration, and parameter continuity during automatic camera switch. If the system detects that the zoom ranges of the two cameras are different during camera switching, it will notify the application through the **isDeviceCapabilityChanged** field in [AutoDeviceSwitchStatus](arkts-camera-camera-autodeviceswitchstatus-i.md). However, the application still needs to handle the UX change. For example, for the zoom range adjustment, the application needs to call [getZoomRatioRange](arkts-camera-camera-zoomquery-i.md#getzoomratiorange) to obtain data and update the UX. Therefore, **AutoDeviceSwitch** is more applicable to simplified UX interactions.

**Inheritance/Implementation:** AutoDeviceSwitch extends [AutoDeviceSwitchQuery](arkts-camera-camera-autodeviceswitchquery-i.md)

**Since:** 13

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## enableAutoDeviceSwitch

```TypeScript
enableAutoDeviceSwitch(enabled: boolean): void
```

Enables or disables automatic camera switch. You can use [isAutoDeviceSwitchSupported](arkts-camera-camera-autodeviceswitchquery-i.md#isautodeviceswitchsupported) to check whether the device supports automatic camera switch.

> **NOTE:** 
> 
> This API is used only for foldable devices with multiple front cameras. In different fold states, the system
> can automatically switch to an available front camera. It does not enable automatic switching between front and
> rear cameras.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable automatic camera switch. **true** to enable, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameters verification failed.<br>**Applicable version:** 19 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function enableAutoDeviceSwitch(session: camera.PhotoSession, isEnable: boolean): void {
  try {
    session.enableAutoDeviceSwitch(isEnable);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The enableAutoDeviceSwitch call failed, error code: ${err.code}, error message: ${err.message}`);
  }
}
```
