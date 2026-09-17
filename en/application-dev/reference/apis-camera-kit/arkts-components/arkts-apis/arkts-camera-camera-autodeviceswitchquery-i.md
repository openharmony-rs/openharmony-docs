# AutoDeviceSwitchQuery

**AutoDeviceSwitchQuery** is used to check whether a device supports automatic camera switch.

[Automatic Camera Switching](arkts-camera-camera-autodeviceswitch-i.md#enableautodeviceswitch) is supported only on foldable devices. For details about how to enable this capability, see [enableAutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md#enableautodeviceswitch).

**Since:** 13

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isAutoDeviceSwitchSupported

```TypeScript
isAutoDeviceSwitchSupported(): boolean
```

Checks whether the device supports automatic camera switch.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of automatic camera switch. **true** if supported, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config, only throw in session usage.<br>**Applicable version:** 13 - 17 |
