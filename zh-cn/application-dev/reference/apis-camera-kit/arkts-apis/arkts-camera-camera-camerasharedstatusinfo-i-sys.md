# CameraSharedStatusInfo（系统接口）

```TypeScript
interface CameraSharedStatusInfo
```

相机共享状态信息。

**起始版本：** 26.0.1

<!--Device-camera-interface CameraSharedStatusInfo--><!--Device-camera-interface CameraSharedStatusInfo-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## camera

```TypeScript
camera: CameraDevice
```

相机实例。

**类型：** [CameraDevice](arkts-camera-camera-cameradevice-i.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CameraSharedStatusInfo-camera: CameraDevice--><!--Device-CameraSharedStatusInfo-camera: CameraDevice-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## sharedStatus

```TypeScript
sharedStatus: CameraSharedStatus
```

当前相机共享状态。

**类型：** [CameraSharedStatus](arkts-camera-camera-camerasharedstatus-e-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CameraSharedStatusInfo-sharedStatus: CameraSharedStatus--><!--Device-CameraSharedStatusInfo-sharedStatus: CameraSharedStatus-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
