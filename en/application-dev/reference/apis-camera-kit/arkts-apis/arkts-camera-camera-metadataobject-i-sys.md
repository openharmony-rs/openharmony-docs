# MetadataObject

Describes the camera metadata, which is the data source of [CameraInput](arkts-camera-camera-camerainput-i.md). The metadata is obtained through **metadataOutput.on('metadataObjectsAvailable')**.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## confidence

```TypeScript
readonly confidence: number
```

Confidence of the detection, with a value range of [0, 1].

**Type:** number

**Since:** 13

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## objectId

```TypeScript
readonly objectId: number
```

Metadata object ID.

**Type:** number

**Since:** 13

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.
