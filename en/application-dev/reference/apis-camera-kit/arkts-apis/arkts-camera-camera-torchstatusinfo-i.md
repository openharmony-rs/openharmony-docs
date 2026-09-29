# TorchStatusInfo

```TypeScript
interface TorchStatusInfo
```

Describes the flashlight status information.

**Since:** 11

<!--Device-camera-interface TorchStatusInfo--><!--Device-camera-interface TorchStatusInfo-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isTorchActive

```TypeScript
readonly isTorchActive: boolean
```

Whether the flashlight is activated. **true** if activated, **false** otherwise.

**Type:** boolean

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-TorchStatusInfo-readonly isTorchActive: boolean--><!--Device-TorchStatusInfo-readonly isTorchActive: boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## isTorchAvailable

```TypeScript
readonly isTorchAvailable: boolean
```

Whether the flashlight is available. **true** if available, **false** otherwise.

**Type:** boolean

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-TorchStatusInfo-readonly isTorchAvailable: boolean--><!--Device-TorchStatusInfo-readonly isTorchAvailable: boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## torchLevel

```TypeScript
readonly torchLevel: number
```

Flashlight brightness level. The value range is [0, 1]. A larger value indicates a greater luminance.

**Type:** number

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-TorchStatusInfo-readonly torchLevel: double--><!--Device-TorchStatusInfo-readonly torchLevel: double-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
