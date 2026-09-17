# CameraOcclusionDetectionResult

Describes the instance returned by the occlusion status callback, which indicates whether the camera lens is blocked or dirty.

**Since:** 23

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

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Camera.Core

## isCameraOccluded

```TypeScript
readonly isCameraOccluded: boolean
```

Whether the camera lens is blocked. **true** if blocked, **false** otherwise.

**Type:** boolean

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Camera.Core
