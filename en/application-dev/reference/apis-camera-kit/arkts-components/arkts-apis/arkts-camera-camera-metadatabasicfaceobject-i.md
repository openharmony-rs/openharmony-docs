# MetadataBasicFaceObject

Basic face metadata detected by the camera, which is extended from [MetadataObject](arkts-camera-camera-metadataobject-i.md). It serves as the data source of the camera information in [CameraInput](arkts-camera-camera-camerainput-i.md). It is obtained by calling metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#onmetadataobjectsavailable).

**Inheritance/Implementation:** MetadataBasicFaceObject extends [MetadataObject](arkts-camera-camera-metadataobject-i.md)

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## leftEyeBoundingBox

```TypeScript
readonly leftEyeBoundingBox?: Rect
```

Left eye area.

**Type:** [Rect](arkts-camera-camera-rect-i.md)

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

## pitchAngle

```TypeScript
readonly pitchAngle?: number
```

Pitch angle. The value range is [-90, 90], with the positive direction being downwards.

**Type:** number

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

## rightEyeBoundingBox

```TypeScript
readonly rightEyeBoundingBox?: Rect
```

Right eye area.

**Type:** [Rect](arkts-camera-camera-rect-i.md)

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

## rollAngle

```TypeScript
readonly rollAngle?: number
```

Roll angle. The value range is [-180, 180], with the positive direction being clockwise.

**Type:** number

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

## yawAngle

```TypeScript
readonly yawAngle?: number
```

Yaw angle. The value range is [-90, 90], with the positive direction being rightwards.

**Type:** number

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core
