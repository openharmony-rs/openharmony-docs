# CaptureStartInfo

```TypeScript
interface CaptureStartInfo
```

Describes the capture start information.

**Since:** 11

<!--Device-camera-interface CaptureStartInfo--><!--Device-camera-interface CaptureStartInfo-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## captureId

```TypeScript
captureId: number
```

ID of this capture action.

**Type:** number

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-CaptureStartInfo-captureId: int--><!--Device-CaptureStartInfo-captureId: int-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## time

```TypeScript
time: number
```

Estimated duration when the sensor captures frames at the bottom layer in a single capture. If **-1** is reported, there is no estimated duration.

**Type:** number

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-CaptureStartInfo-time: long--><!--Device-CaptureStartInfo-time: long-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
