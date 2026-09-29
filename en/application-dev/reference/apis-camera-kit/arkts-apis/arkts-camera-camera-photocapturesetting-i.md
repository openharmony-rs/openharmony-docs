# PhotoCaptureSetting

```TypeScript
interface PhotoCaptureSetting
```

Describes the settings for taking an image.

**Since:** 10

<!--Device-camera-interface PhotoCaptureSetting--><!--Device-camera-interface PhotoCaptureSetting-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## compressionQuality

```TypeScript
compressionQuality?: number
```

Photo image compression quality.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-PhotoCaptureSetting-compressionQuality?: int--><!--Device-PhotoCaptureSetting-compressionQuality?: int-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## location

```TypeScript
location?: Location
```

Geolocation information of the image (depending on the device hardware information by default).

**Type:** [Location](arkts-camera-camera-location-i.md)

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-PhotoCaptureSetting-location?: Location--><!--Device-PhotoCaptureSetting-location?: Location-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## mirror

```TypeScript
mirror?: boolean
```

Whether mirror photography is enabled (disabled by default). Before using this enumerated value, call [isMirrorSupported](arkts-camera-camera-photooutput-i.md#ismirrorsupported) to check whether mirror photography is supported. **true** if enabled, **false** otherwise.

**Type:** boolean

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-PhotoCaptureSetting-mirror?: boolean--><!--Device-PhotoCaptureSetting-mirror?: boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## quality

```TypeScript
quality?: QualityLevel
```

Image quality (high by default).

**Type:** [QualityLevel](arkts-camera-camera-qualitylevel-e.md)

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-PhotoCaptureSetting-quality?: QualityLevel--><!--Device-PhotoCaptureSetting-quality?: QualityLevel-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## rotation

```TypeScript
rotation?: ImageRotation
```

Rotation angle of the image. The default value is **0**, indicating clockwise rotation.

**Type:** [ImageRotation](arkts-camera-camera-imagerotation-e.md)

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-PhotoCaptureSetting-rotation?: ImageRotation--><!--Device-PhotoCaptureSetting-rotation?: ImageRotation-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
