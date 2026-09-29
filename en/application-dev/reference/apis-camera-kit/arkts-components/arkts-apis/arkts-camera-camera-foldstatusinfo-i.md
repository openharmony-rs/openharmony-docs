# FoldStatusInfo

```TypeScript
interface FoldStatusInfo
```

Describes the fold state information about a foldable device.

**Since:** 12

<!--Device-camera-interface FoldStatusInfo--><!--Device-camera-interface FoldStatusInfo-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-FoldStatusInfo-readonly foldStatus: FoldStatus--><!--Device-FoldStatusInfo-readonly foldStatus: FoldStatus-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## supportedCameras

```TypeScript
readonly supportedCameras: Array<CameraDevice>
```

List of cameras supported in the current fold state.

**Type:** Array&lt;[CameraDevice](arkts-camera-camera-cameradevice-i.md)&gt;

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-FoldStatusInfo-readonly supportedCameras: Array<CameraDevice>--><!--Device-FoldStatusInfo-readonly supportedCameras: Array<CameraDevice>-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
