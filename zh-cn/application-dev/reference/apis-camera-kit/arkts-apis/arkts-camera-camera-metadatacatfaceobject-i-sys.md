# MetadataCatFaceObject（系统接口）

相机检测到的猫脸元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md#MetadataObject)。[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)相机信息中的数据来源，通过 metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#on_metadataObjectsAvailable) 接口获取。

**继承/实现关系：** MetadataCatFaceObject extends [MetadataObject](arkts-camera-camera-metadataobject-i.md#MetadataObject)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface MetadataCatFaceObject--><!--Device-camera-interface MetadataCatFaceObject-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## leftEyeBoundingBox

```TypeScript
readonly leftEyeBoundingBox: Rect
```

左眼区域框。

**类型：** Rect

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataCatFaceObject-readonly leftEyeBoundingBox: Rect--><!--Device-MetadataCatFaceObject-readonly leftEyeBoundingBox: Rect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## rightEyeBoundingBox

```TypeScript
readonly rightEyeBoundingBox: Rect
```

右眼区域框。

**类型：** Rect

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataCatFaceObject-readonly rightEyeBoundingBox: Rect--><!--Device-MetadataCatFaceObject-readonly rightEyeBoundingBox: Rect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

