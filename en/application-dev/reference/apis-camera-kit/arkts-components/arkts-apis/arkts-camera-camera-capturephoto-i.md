# CapturePhoto

```TypeScript
interface CapturePhoto
```

**CapturePhoto** provides APIs for obtaining the objects of the full-quality image and the uncompressed image.

**Since:** 23

<!--Device-camera-interface CapturePhoto--><!--Device-camera-interface CapturePhoto-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## release

```TypeScript
release(): Promise<void>
```

Releases output resources. This API uses a promise to return the result. Model constraint: This API can be used only in the stage model.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-CapturePhoto-release(): Promise<void>--><!--Device-CapturePhoto-release(): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { camera } from '@kit.CameraKit';

async function releaseCapturePhoto(capturePhoto: camera.CapturePhoto): Promise<void> {
  await capturePhoto.release();
}
```

## main

```TypeScript
main: ImageType
```

Object of the full-quality image and the uncompressed image.

**Type:** [ImageType](arkts-camera-camera-imagetype-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-CapturePhoto-main: ImageType--><!--Device-CapturePhoto-main: ImageType-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## oxygenPhoto

```TypeScript
oxygenPhoto?: ImageType
```

Object of the oxygen auxiliary photo.

**Type:** [ImageType](arkts-camera-camera-imagetype-t.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.1.

<!--Device-CapturePhoto-oxygenPhoto?: ImageType--><!--Device-CapturePhoto-oxygenPhoto?: ImageType-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## pigmentationPhoto

```TypeScript
pigmentationPhoto?: ImageType
```

Object of the pigmentation auxiliary photo.

**Type:** [ImageType](arkts-camera-camera-imagetype-t.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.1.

<!--Device-CapturePhoto-pigmentationPhoto?: ImageType--><!--Device-CapturePhoto-pigmentationPhoto?: ImageType-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
