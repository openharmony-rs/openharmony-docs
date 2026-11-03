# PrelaunchConfig（系统接口）

```TypeScript
interface PrelaunchConfig
```

相机预启动配置信息。目前该配置用于传感器级预启动，后续版本将用于流级预启动。

**起始版本：** 10

<!--Device-camera-interface PrelaunchConfig--><!--Device-camera-interface PrelaunchConfig-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## activeTime

```TypeScript
activeTime?: number
```

激活时间。单位：分钟。

**类型：** number

**起始版本：** 11

<!--Device-PrelaunchConfig-activeTime?: int--><!--Device-PrelaunchConfig-activeTime?: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## cameraDevice

```TypeScript
cameraDevice: CameraDevice
```

相机设备。

**类型：** [CameraDevice](arkts-camera-camera-cameradevice-i.md)

**起始版本：** 10

<!--Device-PrelaunchConfig-cameraDevice: CameraDevice--><!--Device-PrelaunchConfig-cameraDevice: CameraDevice-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## restoreParamType

```TypeScript
restoreParamType?: RestoreParamType
```

预启动使用的参数类型。

**类型：** [RestoreParamType](arkts-camera-camera-restoreparamtype-e-sys.md)

**起始版本：** 11

<!--Device-PrelaunchConfig-restoreParamType?: RestoreParamType--><!--Device-PrelaunchConfig-restoreParamType?: RestoreParamType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## settingParam

```TypeScript
settingParam?: SettingParam
```

设置参数。

**类型：** [SettingParam](arkts-camera-camera-settingparam-i-sys.md)

**起始版本：** 11

<!--Device-PrelaunchConfig-settingParam?: SettingParam--><!--Device-PrelaunchConfig-settingParam?: SettingParam-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
