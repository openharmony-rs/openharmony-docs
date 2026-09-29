# QuickThumbnail (System API)

```TypeScript
interface QuickThumbnail
```

Quick thumbnail object

**Since:** 19

<!--Device-camera-interface QuickThumbnail--><!--Device-camera-interface QuickThumbnail-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## release

```TypeScript
release(): Promise<void>
```

Release quick thumbnail object.

**Since:** 19

<!--Device-QuickThumbnail-release(): Promise<void>--><!--Device-QuickThumbnail-release(): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

## captureId

```TypeScript
readonly captureId: number
```

capture id.

**Type:** number

**Since:** 19

<!--Device-QuickThumbnail-readonly captureId: int--><!--Device-QuickThumbnail-readonly captureId: int-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## thumbnailImage

```TypeScript
thumbnailImage: image.PixelMap
```

Thumbnail image.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 19

<!--Device-QuickThumbnail-thumbnailImage: image.PixelMap--><!--Device-QuickThumbnail-thumbnailImage: image.PixelMap-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.
