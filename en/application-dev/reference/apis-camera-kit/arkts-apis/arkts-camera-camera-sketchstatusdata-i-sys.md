# SketchStatusData (System API)

Defines the PiP status data.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## centerPointOffset

```TypeScript
centerPointOffset: Point
```

Offset of PiP.

**Type:** [Point](arkts-camera-camera-point-i.md)

**Since:** 20

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## sketchRatio

```TypeScript
sketchRatio: number
```

Zoom ratio of PiP.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## status

```TypeScript
status: number
```

Status of PiP. The options are 0 (stopped), 1 (started), 2 (stopping), and 3 (starting).

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.
