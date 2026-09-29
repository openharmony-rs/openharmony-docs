# ControlCenterStatusInfo

```TypeScript
interface ControlCenterStatusInfo
```

相机控制器效果激活状态信息。

**起始版本：** 20

<!--Device-camera-interface ControlCenterStatusInfo--><!--Device-camera-interface ControlCenterStatusInfo-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## effectType

```TypeScript
readonly effectType: ControlCenterEffectType
```

相机控制器效果类型。

**类型：** [ControlCenterEffectType](arkts-camera-camera-controlcentereffecttype-e.md)

**起始版本：** 20

**原子化服务API（仅ArkTS-Dyn）：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-ControlCenterStatusInfo-readonly effectType: ControlCenterEffectType--><!--Device-ControlCenterStatusInfo-readonly effectType: ControlCenterEffectType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isActive

```TypeScript
readonly isActive: boolean
```

相机控制器效果激活状态。true表示已激活，false表示未激活。

**类型：** boolean

**起始版本：** 20

**原子化服务API（仅ArkTS-Dyn）：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-ControlCenterStatusInfo-readonly isActive: boolean--><!--Device-ControlCenterStatusInfo-readonly isActive: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core
