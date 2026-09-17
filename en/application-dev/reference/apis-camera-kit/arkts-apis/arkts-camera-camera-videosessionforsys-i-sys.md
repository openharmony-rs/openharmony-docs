# VideoSessionForSys (System API)

Implements a video session for system applications, which sets the parameters of the normal video mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md).

@extends VideoSession, Beauty, ColorEffect, ColorManagement, Macro [since 11 - 14] @extends VideoSession, Beauty, ColorEffect, ColorManagement, Macro, Aperture, ColorReservation [since 15 - 17] @extends VideoSession, Beauty, ColorEffect, ColorManagement, Macro, Aperture, ColorReservation, EffectSuggestion [since 18] @extends VideoSession, Beauty, ColorEffect, ColorManagement, Macro, Aperture, ColorReservation, EffectSuggestion, ImagingMode [since 26.1.0]

**Inheritance/Implementation:** VideoSessionForSys extends [VideoSession](arkts-camera-camera-videosession-i.md)<!--Del-->, [Beauty](arkts-camera-camera-beauty-i-sys.md)<!--DelEnd--><!--Del-->, [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md)<!--DelEnd-->, [ColorManagement](arkts-camera-camera-colormanagement-i.md), [Macro](arkts-camera-camera-macro-i.md), [Aperture](arkts-camera-camera-aperture-i.md)<!--Del-->, [ColorReservation](arkts-camera-camera-colorreservation-i-sys.md)<!--DelEnd--><!--Del-->, [EffectSuggestion](arkts-camera-camera-effectsuggestion-i-sys.md)<!--DelEnd--><!--Del-->, [ImagingMode](arkts-camera-camera-imagingmode-i-sys.md)<!--DelEnd-->

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```
