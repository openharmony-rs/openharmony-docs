# AutoDeviceSwitchStatus

```TypeScript
interface AutoDeviceSwitchStatus
```

Describes the information about the automatic camera switch status.

**Since:** 13

<!--Device-camera-interface AutoDeviceSwitchStatus--><!--Device-camera-interface AutoDeviceSwitchStatus-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isDeviceCapabilityChanged

```TypeScript
readonly isDeviceCapabilityChanged: boolean
```

Whether the camera capability is changed after the camera is automatically switched. **true** if changed, **false** otherwise.

**Type:** boolean

**Since:** 13

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-AutoDeviceSwitchStatus-readonly isDeviceCapabilityChanged: boolean--><!--Device-AutoDeviceSwitchStatus-readonly isDeviceCapabilityChanged: boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## isDeviceSwitched

```TypeScript
readonly isDeviceSwitched: boolean
```

Whether the camera is automatically switched. **true** if auto-switched, **false** otherwise.

**Type:** boolean

**Since:** 13

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-AutoDeviceSwitchStatus-readonly isDeviceSwitched: boolean--><!--Device-AutoDeviceSwitchStatus-readonly isDeviceSwitched: boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
