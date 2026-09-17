# FoldStatusInfo

Describes the fold state information about a foldable device.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## foldStatus

```TypeScript
readonly foldStatus: FoldStatus
```

Fold state.

**Type:** [FoldStatus](arkts-camera-camera-foldstatus-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## supportedCameras

```TypeScript
readonly supportedCameras: Array<CameraDevice>
```

List of cameras supported in the current fold state.

**Type:** Array&lt;[CameraDevice](arkts-camera-camera-cameradevice-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core
