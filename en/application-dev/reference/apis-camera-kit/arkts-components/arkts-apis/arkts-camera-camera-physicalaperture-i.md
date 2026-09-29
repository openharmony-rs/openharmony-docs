# PhysicalAperture

```TypeScript
interface PhysicalAperture
```

Describes the physical aperture object.

**Since:** 24

<!--Device-camera-interface PhysicalAperture--><!--Device-camera-interface PhysicalAperture-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## apertures

```TypeScript
apertures: Array<number>
```

Supported physical aperture.

**Type:** Array&lt;number&gt;

**Since:** 24

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-PhysicalAperture-apertures: Array<double>--><!--Device-PhysicalAperture-apertures: Array<double>-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## zoomRange

```TypeScript
zoomRange: ZoomRange
```

Zoom range of a given physical aperture.

**Type:** [ZoomRange](arkts-camera-camera-zoomrange-i.md)

**Since:** 24

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-PhysicalAperture-zoomRange: ZoomRange--><!--Device-PhysicalAperture-zoomRange: ZoomRange-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
