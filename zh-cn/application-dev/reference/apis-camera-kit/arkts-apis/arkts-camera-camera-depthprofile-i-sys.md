# DepthProfile（系统接口）

```TypeScript
interface DepthProfile
```

描述深度数据的 profile。继承自 [Profile](arkts-camera-camera-profile-i.md)。

**起始版本：** 13

<!--Device-camera-interface DepthProfile--><!--Device-camera-interface DepthProfile-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## dataAccuracy

```TypeScript
readonly dataAccuracy: DepthDataAccuracy
```

深度数据的精度，可以是相对精度或绝对精度。

**类型：** [DepthDataAccuracy](arkts-camera-camera-depthdataaccuracy-e-sys.md)

**起始版本：** 13

<!--Device-DepthProfile-readonly dataAccuracy: DepthDataAccuracy--><!--Device-DepthProfile-readonly dataAccuracy: DepthDataAccuracy-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## format

```TypeScript
readonly format: CameraFormat
```

相机输出格式。

**类型：** [CameraFormat](arkts-camera-camera-cameraformat-e.md)

**起始版本：** 13

<!--Device-DepthProfile-readonly format: CameraFormat--><!--Device-DepthProfile-readonly format: CameraFormat-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## size

```TypeScript
readonly size: Size
```

深度数据分辨率。

**类型：** Size

**起始版本：** 13

<!--Device-DepthProfile-readonly size: Size--><!--Device-DepthProfile-readonly size: Size-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
