# FocusTrackingInfo (System API)

Describes the focus tracking information, which is obtained by calling VideoSessionForSys. [on('focusTrackingInfoAvailable')](arkts-camera-camera-videosession-i-sys.md#onfocustrackinginfoavailable).

**Since:** 15

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## trackingMode

```TypeScript
trackingMode: FocusTrackingMode
```

Tracing mode.

**Type:** [FocusTrackingMode](arkts-camera-camera-focustrackingmode-e-sys.md)

**Since:** 15

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## trackingRegion

```TypeScript
trackingRegion: Rect
```

Tracking region.

**Type:** [Rect](arkts-camera-camera-rect-i.md)

**Since:** 15

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.
