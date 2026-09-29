# MetadataCatFaceObject

```TypeScript
interface MetadataCatFaceObject extends MetadataObject
```

Cat face metadata detected by the camera, which is extended from [MetadataObject](arkts-camera-camera-metadataobject-i.md). It serves as the data source of the camera information in [CameraInput](arkts-camera-camera-camerainput-i.md). It is obtained by calling metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#onmetadataobjectsavailable).

**Inheritance/Implementation:** MetadataCatFaceObject extends [MetadataObject](arkts-camera-camera-metadataobject-i.md)

**Since:** 26.0.0

<!--Device-camera-interface MetadataCatFaceObject extends MetadataObject--><!--Device-camera-interface MetadataCatFaceObject extends MetadataObject-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## leftEyeBoundingBox

```TypeScript
readonly leftEyeBoundingBox: Rect
```

Left eye area.

**Type:** [Rect](arkts-camera-camera-rect-i.md)

**Since:** 26.0.0

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-MetadataCatFaceObject-readonly leftEyeBoundingBox: Rect--><!--Device-MetadataCatFaceObject-readonly leftEyeBoundingBox: Rect-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## rightEyeBoundingBox

```TypeScript
readonly rightEyeBoundingBox: Rect
```

Right eye area.

**Type:** [Rect](arkts-camera-camera-rect-i.md)

**Since:** 26.0.0

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-MetadataCatFaceObject-readonly rightEyeBoundingBox: Rect--><!--Device-MetadataCatFaceObject-readonly rightEyeBoundingBox: Rect-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
