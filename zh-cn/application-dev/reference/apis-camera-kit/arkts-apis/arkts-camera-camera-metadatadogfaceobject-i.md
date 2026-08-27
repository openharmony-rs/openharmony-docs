# MetadataDogFaceObject

相机检测到的狗脸元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md)。[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过 metadataOutput. on('metadataObjectsAvailable') 接口获取。

**继承/实现关系：** MetadataDogFaceObject extends [MetadataObject](arkts-camera-camera-metadataobject-i.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## leftEyeBoundingBox

```TypeScript
readonly leftEyeBoundingBox: Rect
```

左眼区域框。

**类型：** Rect

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## rightEyeBoundingBox

```TypeScript
readonly rightEyeBoundingBox: Rect
```

右眼区域框。

**类型：** Rect

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core
