# DepthData（系统接口）

Describes a depth data object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface DepthData--><!--Device-camera-interface DepthData-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## release

```TypeScript
release(): Promise<void>
```

Releases depth data output resources. This API uses a promise to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DepthData-release(): Promise<void>--><!--Device-DepthData-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

**类型：** [DepthDataAccuracy](arkts-camera-camera-depthdataaccuracy-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DepthData-readonly dataAccuracy: DepthDataAccuracy--><!--Device-DepthData-readonly dataAccuracy: DepthDataAccuracy-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## depthMap

```TypeScript
readonly depthMap: image.PixelMap
```

Depth map.

**类型：** image.PixelMap

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DepthData-readonly depthMap: image.PixelMap--><!--Device-DepthData-readonly depthMap: image.PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## format

```TypeScript
readonly format: CameraFormat
```

Camera output format.

**类型：** [CameraFormat](arkts-camera-camera-cameraformat-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DepthData-readonly format: CameraFormat--><!--Device-DepthData-readonly format: CameraFormat-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## qualityLevel

```TypeScript
readonly qualityLevel: DepthDataQualityLevel
```

Quality level of the depth map.

**类型：** [DepthDataQualityLevel](arkts-camera-camera-depthdataqualitylevel-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DepthData-readonly qualityLevel: DepthDataQualityLevel--><!--Device-DepthData-readonly qualityLevel: DepthDataQualityLevel-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

