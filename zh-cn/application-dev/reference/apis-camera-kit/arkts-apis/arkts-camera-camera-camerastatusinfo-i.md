# CameraStatusInfo

相机管理器回调返回的接口实例，该实例表示相机状态信息。

**起始版本：** 23

<!--Device-camera-interface CameraStatusInfo--><!--Device-camera-interface CameraStatusInfo-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## camera

```TypeScript
camera: CameraDevice
```

相机信息。

**类型：** [CameraDevice](arkts-camera-camera-cameradevice-i.md)

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraStatusInfo-camera: CameraDevice--><!--Device-CameraStatusInfo-camera: CameraDevice-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## status

```TypeScript
status: CameraStatus
```

相机状态。

**类型：** [CameraStatus](arkts-camera-camera-camerastatus-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraStatusInfo-status: CameraStatus--><!--Device-CameraStatusInfo-status: CameraStatus-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

