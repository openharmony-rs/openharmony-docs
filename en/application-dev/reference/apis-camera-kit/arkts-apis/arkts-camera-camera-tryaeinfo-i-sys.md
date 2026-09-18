# TryAEInfo (System API)

Describes the Try AE parameters. Try AE indicates that the hardware reports the status based on the ambient illumination change during time-lapse photographing.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## captureInterval

```TypeScript
readonly captureInterval?: number
```

Timelapse capture interval.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## isTryAEDone

```TypeScript
readonly isTryAEDone: boolean
```

Determine whether try AE is done.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## isTryAEHintNeeded

```TypeScript
readonly isTryAEHintNeeded?: boolean
```

Determine whether AE hint is needed.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## previewType

```TypeScript
readonly previewType?: TimeLapsePreviewType
```

Timelapse preview type.

**Type:** [TimeLapsePreviewType](arkts-camera-camera-timelapsepreviewtype-e-sys.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.
