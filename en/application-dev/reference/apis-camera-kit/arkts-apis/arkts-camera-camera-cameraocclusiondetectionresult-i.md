# CameraOcclusionDetectionResult

```TypeScript
interface CameraOcclusionDetectionResult
```

Describes the instance returned by the occlusion status callback, which indicates whether the camera lens is blocked or dirty.

**Since:** 23

<!--Device-camera-interface CameraOcclusionDetectionResult--><!--Device-camera-interface CameraOcclusionDetectionResult-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isCameraLensDirty

```TypeScript
readonly isCameraLensDirty: boolean
```

Whether the camera lens is dirty. **true** if dirty, false otherwise.

**Type:** boolean

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-CameraOcclusionDetectionResult-readonly isCameraLensDirty: boolean--><!--Device-CameraOcclusionDetectionResult-readonly isCameraLensDirty: boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## isCameraOccluded

```TypeScript
readonly isCameraOccluded: boolean
```

Whether the camera lens is blocked. **true** if blocked, **false** otherwise.

**Type:** boolean

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-CameraOcclusionDetectionResult-readonly isCameraOccluded: boolean--><!--Device-CameraOcclusionDetectionResult-readonly isCameraOccluded: boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
