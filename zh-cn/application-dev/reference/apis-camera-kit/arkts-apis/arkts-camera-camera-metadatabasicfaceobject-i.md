# MetadataBasicFaceObject

相机检测到的基础人脸元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md)。[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源， 通过metadataOutput. on('metadataObjectsAvailable') 接口获取。

**继承/实现关系：** MetadataBasicFaceObject extends [MetadataObject](arkts-camera-camera-metadataobject-i.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## leftEyeBoundingBox

```TypeScript
readonly leftEyeBoundingBox?: Rect
```

左眼区域框。

**类型：** Rect

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## pitchAngle

```TypeScript
readonly pitchAngle?: number
```

俯仰角度。取值范围为[-90, 90]，以向下为正方向。

**类型：** number

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## rightEyeBoundingBox

```TypeScript
readonly rightEyeBoundingBox?: Rect
```

右眼区域框。

**类型：** Rect

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## rollAngle

```TypeScript
readonly rollAngle?: number
```

平面内旋转角度。取值范围为[-180, 180]，以顺时针方向为正方向。

**类型：** number

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## yawAngle

```TypeScript
readonly yawAngle?: number
```

左右旋转角度。取值范围为[-90, 90]，以向右为正方向。

**类型：** number

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core
