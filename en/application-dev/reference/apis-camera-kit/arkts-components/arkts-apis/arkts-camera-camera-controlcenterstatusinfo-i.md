# ControlCenterStatusInfo

```TypeScript
interface ControlCenterStatusInfo
```

Describes the effect status information of a camera controller.

**Since:** 20

<!--Device-camera-interface ControlCenterStatusInfo--><!--Device-camera-interface ControlCenterStatusInfo-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## effectType

```TypeScript
readonly effectType: ControlCenterEffectType
```

Effect type of the camera controller.

**Type:** [ControlCenterEffectType](arkts-camera-camera-controlcentereffecttype-e.md)

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-ControlCenterStatusInfo-readonly effectType: ControlCenterEffectType--><!--Device-ControlCenterStatusInfo-readonly effectType: ControlCenterEffectType-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## isActive

```TypeScript
readonly isActive: boolean
```

Whether the camera controller is activated. **true** if activated, **false** otherwise.

**Type:** boolean

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-ControlCenterStatusInfo-readonly isActive: boolean--><!--Device-ControlCenterStatusInfo-readonly isActive: boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
