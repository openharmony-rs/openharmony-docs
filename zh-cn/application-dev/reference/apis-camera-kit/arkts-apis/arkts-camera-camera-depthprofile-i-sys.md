# DepthProfile（系统接口）

Describes the profile of depth data. It inherits from [Profile](arkts-camera-camera-profile-i.md).

**起始版本：** 23

<!--Device-camera-interface DepthProfile--><!--Device-camera-interface DepthProfile-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## dataAccuracy

```TypeScript
readonly dataAccuracy: DepthDataAccuracy
```

Accuracy of the depth data, which can be either relative accuracy or absolute accuracy.

**类型：** [DepthDataAccuracy](arkts-camera-camera-depthdataaccuracy-e-sys.md)

**起始版本：** 23

<!--Device-DepthProfile-readonly dataAccuracy: DepthDataAccuracy--><!--Device-DepthProfile-readonly dataAccuracy: DepthDataAccuracy-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## format

```TypeScript
readonly format: CameraFormat
```

Camera output format.

**类型：** [CameraFormat](arkts-camera-camera-cameraformat-e.md)

**起始版本：** 23

<!--Device-DepthProfile-readonly format: CameraFormat--><!--Device-DepthProfile-readonly format: CameraFormat-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## size

```TypeScript
readonly size: Size
```

Depth data resolution.

**类型：** Size

**起始版本：** 23

<!--Device-DepthProfile-readonly size: Size--><!--Device-DepthProfile-readonly size: Size-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

