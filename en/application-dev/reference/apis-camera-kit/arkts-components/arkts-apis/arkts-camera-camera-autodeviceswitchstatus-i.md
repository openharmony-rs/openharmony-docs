# AutoDeviceSwitchStatus

Describes the information about the automatic camera switch status.

**Since:** 13

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

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## isDeviceSwitched

```TypeScript
readonly isDeviceSwitched: boolean
```

Whether the camera is automatically switched. **true** if auto-switched, **false** otherwise.

**Type:** boolean

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core
