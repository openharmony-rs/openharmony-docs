# DepthData (System API)

```TypeScript
interface DepthData
```

Describes a depth data object.

**Since:** 13

<!--Device-camera-interface DepthData--><!--Device-camera-interface DepthData-End-->

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

Releases depth data output resources. This API uses a promise to return the result.

**Since:** 13

<!--Device-DepthData-release(): Promise<void>--><!--Device-DepthData-release(): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

**Examples**

```TypeScript
async function releaseDepthData(depthData: camera.DepthData): Promise<void> {
  await depthData.release();
}
```

## dataAccuracy

```TypeScript
readonly dataAccuracy: DepthDataAccuracy
```

Accuracy of the depth data, which can be either relative accuracy or absolute accuracy.

**Type:** [DepthDataAccuracy](arkts-camera-camera-depthdataaccuracy-e-sys.md)

**Since:** 13

<!--Device-DepthData-readonly dataAccuracy: DepthDataAccuracy--><!--Device-DepthData-readonly dataAccuracy: DepthDataAccuracy-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## depthMap

```TypeScript
readonly depthMap: image.PixelMap
```

Depth map.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 13

<!--Device-DepthData-readonly depthMap: image.PixelMap--><!--Device-DepthData-readonly depthMap: image.PixelMap-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## format

```TypeScript
readonly format: CameraFormat
```

Camera output format.

**Type:** [CameraFormat](arkts-camera-camera-cameraformat-e.md)

**Since:** 13

<!--Device-DepthData-readonly format: CameraFormat--><!--Device-DepthData-readonly format: CameraFormat-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## qualityLevel

```TypeScript
readonly qualityLevel: DepthDataQualityLevel
```

Quality level of the depth map.

**Type:** [DepthDataQualityLevel](arkts-camera-camera-depthdataqualitylevel-e-sys.md)

**Since:** 13

<!--Device-DepthData-readonly qualityLevel: DepthDataQualityLevel--><!--Device-DepthData-readonly qualityLevel: DepthDataQualityLevel-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.
