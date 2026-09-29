# CameraConcurrentInfo

```TypeScript
interface CameraConcurrentInfo
```

Describes the camera's concurrency information.

**Since:** 18

<!--Device-camera-interface CameraConcurrentInfo--><!--Device-camera-interface CameraConcurrentInfo-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## device

```TypeScript
readonly device: CameraDevice
```

Concurrent camera device.

**Type:** [CameraDevice](arkts-camera-camera-cameradevice-i.md)

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-CameraConcurrentInfo-readonly device: CameraDevice--><!--Device-CameraConcurrentInfo-readonly device: CameraDevice-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## modes

```TypeScript
readonly modes: Array<SceneMode>
```

Scene mode.

**Type:** Array&lt;[SceneMode](arkts-camera-camera-scenemode-e.md)&gt;

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-CameraConcurrentInfo-readonly modes: Array<SceneMode>--><!--Device-CameraConcurrentInfo-readonly modes: Array<SceneMode>-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## outputCapabilities

```TypeScript
readonly outputCapabilities: Array<CameraOutputCapability>
```

Output capabilities of the camera.

**Type:** Array&lt;[CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md)&gt;

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-CameraConcurrentInfo-readonly outputCapabilities: Array<CameraOutputCapability>--><!--Device-CameraConcurrentInfo-readonly outputCapabilities: Array<CameraOutputCapability>-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## type

```TypeScript
readonly type: CameraConcurrentType
```

Concurrency type.

**Type:** [CameraConcurrentType](arkts-camera-camera-cameraconcurrenttype-e.md)

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-CameraConcurrentInfo-readonly type: CameraConcurrentType--><!--Device-CameraConcurrentInfo-readonly type: CameraConcurrentType-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
