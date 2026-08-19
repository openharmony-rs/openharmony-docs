# MetadataObject

相机元能力信息，[CameraInput](arkts-camera-camera-camerainput-i.md)相机信息中的数据来源，通过metadataOutput.on('metadataObjectsAvailable')接口获取。

**起始版本：** 23

<!--Device-camera-interface MetadataObject--><!--Device-camera-interface MetadataObject-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## confidence

```TypeScript
readonly confidence: double
```

Confidence of the detection, with a value range of [0, 1].

**类型：** double

**起始版本：** 23

<!--Device-MetadataObject-readonly confidence: double--><!--Device-MetadataObject-readonly confidence: double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## objectId

```TypeScript
readonly objectId: int
```

Metadata object ID.

**类型：** int

**起始版本：** 23

<!--Device-MetadataObject-readonly objectId: int--><!--Device-MetadataObject-readonly objectId: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

