# MetadataDogFaceObject（系统接口）

相机检测到的狗脸元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md)。[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过 metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#onmetadataobjectsavailable) 接口获取。

**继承/实现关系：** MetadataDogFaceObject extends [MetadataObject](arkts-camera-camera-metadataobject-i.md)

**起始版本：** 23

<!--Device-camera-interface MetadataDogFaceObject--><!--Device-camera-interface MetadataDogFaceObject-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## leftEyeBoundingBox

```TypeScript
readonly leftEyeBoundingBox: Rect
```

左眼区域框。

**类型：** Rect

**起始版本：** 23

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataDogFaceObject-readonly leftEyeBoundingBox: Rect--><!--Device-MetadataDogFaceObject-readonly leftEyeBoundingBox: Rect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## rightEyeBoundingBox

```TypeScript
readonly rightEyeBoundingBox: Rect
```

右眼区域框。

**类型：** Rect

**起始版本：** 23

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataDogFaceObject-readonly rightEyeBoundingBox: Rect--><!--Device-MetadataDogFaceObject-readonly rightEyeBoundingBox: Rect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

