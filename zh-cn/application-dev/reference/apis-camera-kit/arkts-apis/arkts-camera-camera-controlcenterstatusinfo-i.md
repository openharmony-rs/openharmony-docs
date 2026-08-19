# ControlCenterStatusInfo

相机控制器效果激活状态信息。

**起始版本：** 23

<!--Device-camera-interface ControlCenterStatusInfo--><!--Device-camera-interface ControlCenterStatusInfo-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## effectType

```TypeScript
readonly effectType: ControlCenterEffectType
```

相机控制器效果类型。

**类型：** [ControlCenterEffectType](arkts-camera-camera-controlcentereffecttype-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ControlCenterStatusInfo-readonly effectType: ControlCenterEffectType--><!--Device-ControlCenterStatusInfo-readonly effectType: ControlCenterEffectType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isActive

```TypeScript
readonly isActive: boolean
```

相机控制器效果激活状态。true表示已激活，false表示未激活。

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ControlCenterStatusInfo-readonly isActive: boolean--><!--Device-ControlCenterStatusInfo-readonly isActive: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

