# Profile

```TypeScript
interface Profile
```

Describes the camera profile.

**Since:** 10

<!--Device-camera-interface Profile--><!--Device-camera-interface Profile-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## format

```TypeScript
readonly format: CameraFormat
```

Output format.

**Type:** [CameraFormat](arkts-camera-camera-cameraformat-e.md)

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-Profile-readonly format: CameraFormat--><!--Device-Profile-readonly format: CameraFormat-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## size

```TypeScript
readonly size: Size
```

Resolution.

The size setting corresponds to the camera's resolution width and height, rather than the actual dimensions of the output image.

**Type:** Size

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-Profile-readonly size: Size--><!--Device-Profile-readonly size: Size-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
