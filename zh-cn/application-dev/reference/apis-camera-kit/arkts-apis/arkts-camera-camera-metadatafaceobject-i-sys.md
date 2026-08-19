# MetadataFaceObject（系统接口）

相机检测到的人脸元数据信息，继承自[MetadataObject](arkts-camera-camera-metadataobject-i.md)。[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过 metadataOutput. [on('metadataObjectsAvailable')](arkts-camera-camera-metadataoutput-i.md#onmetadataobjectsavailable) 接口获取。

**继承/实现关系：** MetadataFaceObject extends [MetadataObject](arkts-camera-camera-metadataobject-i.md)

**起始版本：** 23

<!--Device-camera-interface MetadataFaceObject--><!--Device-camera-interface MetadataFaceObject-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## emotion

```TypeScript
readonly emotion: Emotion
```

检测到的情绪类型。

**类型：** [Emotion](arkts-camera-camera-emotion-e-sys.md)

**起始版本：** 23

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataFaceObject-readonly emotion: Emotion--><!--Device-MetadataFaceObject-readonly emotion: Emotion-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## emotionConfidence

```TypeScript
readonly emotionConfidence: double
```

情绪检测置信度。取值范围为[0, 1]。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataFaceObject-readonly emotionConfidence: double--><!--Device-MetadataFaceObject-readonly emotionConfidence: double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## leftEyeBoundingBox

```TypeScript
readonly leftEyeBoundingBox: Rect
```

左眼区域框。

**类型：** Rect

**起始版本：** 23

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataFaceObject-readonly leftEyeBoundingBox: Rect--><!--Device-MetadataFaceObject-readonly leftEyeBoundingBox: Rect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## pitchAngle

```TypeScript
readonly pitchAngle: int
```

俯仰角度。取值范围为[-90, 90]，以向下为正方向。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataFaceObject-readonly pitchAngle: int--><!--Device-MetadataFaceObject-readonly pitchAngle: int-End-->

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

<!--Device-MetadataFaceObject-readonly rightEyeBoundingBox: Rect--><!--Device-MetadataFaceObject-readonly rightEyeBoundingBox: Rect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## rollAngle

```TypeScript
readonly rollAngle: int
```

平面内旋转角度。取值范围为[-180, 180]，以顺时针方向为正方向。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataFaceObject-readonly rollAngle: int--><!--Device-MetadataFaceObject-readonly rollAngle: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## yawAngle

```TypeScript
readonly yawAngle: int
```

左右旋转角度。取值范围为[-90, 90]，以向右为正方向。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataFaceObject-readonly yawAngle: int--><!--Device-MetadataFaceObject-readonly yawAngle: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

