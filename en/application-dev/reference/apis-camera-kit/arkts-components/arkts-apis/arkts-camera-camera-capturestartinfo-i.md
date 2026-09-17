# CaptureStartInfo

Describes the capture start information.

**Since:** 11

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

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## time

```TypeScript
time: number
```

Estimated duration when the sensor captures frames at the bottom layer in a single capture. If **-1** is reported, there is no estimated duration.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core
