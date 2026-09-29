# Photo

```TypeScript
interface Photo
```

Photo defines a full-quality image object.

**Since:** 11

<!--Device-camera-interface Photo--><!--Device-camera-interface Photo-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## release

```TypeScript
release(): Promise<void>
```

Releases output resources. This API uses a promise to return the result.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-Photo-release(): Promise<void>--><!--Device-Photo-release(): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
async function releasePhoto(photo: camera.Photo): Promise<void> {
  await photo.release();
}
```

## main

```TypeScript
main: image.Image
```

Full-quality image.

**Type:** [image.Image](../../apis-image-kit/arkts-apis/arkts-image-image-image-i.md)

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-Photo-main: image.Image--><!--Device-Photo-main: image.Image-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
