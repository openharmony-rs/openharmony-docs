# DepthData（系统接口）

```TypeScript
interface DepthData
```

描述深度数据对象。

**起始版本：** 13

<!--Device-camera-interface DepthData--><!--Device-camera-interface DepthData-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## release

```TypeScript
release(): Promise<void>
```

释放深度数据输出资源。此接口使用 Promise 返回结果。

**起始版本：** 13

<!--Device-DepthData-release(): Promise<void>--><!--Device-DepthData-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回值的 Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
async function releaseDepthData(depthData: camera.DepthData): Promise<void> {
  await depthData.release();
}
```

<!--DelEnd-->

## dataAccuracy

```TypeScript
readonly dataAccuracy: DepthDataAccuracy
```

深度数据的精度，可以是相对精度或绝对精度。

**类型：** [DepthDataAccuracy](arkts-camera-camera-depthdataaccuracy-e-sys.md)

**起始版本：** 13

<!--Device-DepthData-readonly dataAccuracy: DepthDataAccuracy--><!--Device-DepthData-readonly dataAccuracy: DepthDataAccuracy-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## depthMap

```TypeScript
readonly depthMap: image.PixelMap
```

深度图。

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**起始版本：** 13

<!--Device-DepthData-readonly depthMap: image.PixelMap--><!--Device-DepthData-readonly depthMap: image.PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## format

```TypeScript
readonly format: CameraFormat
```

相机输出格式。

**类型：** [CameraFormat](arkts-camera-camera-cameraformat-e.md)

**起始版本：** 13

<!--Device-DepthData-readonly format: CameraFormat--><!--Device-DepthData-readonly format: CameraFormat-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## qualityLevel

```TypeScript
readonly qualityLevel: DepthDataQualityLevel
```

深度图的质量等级。

**类型：** [DepthDataQualityLevel](arkts-camera-camera-depthdataqualitylevel-e-sys.md)

**起始版本：** 13

<!--Device-DepthData-readonly qualityLevel: DepthDataQualityLevel--><!--Device-DepthData-readonly qualityLevel: DepthDataQualityLevel-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
