# PrelaunchConfig (System API)

Defines the camera prelaunch configuration. Currently, the configuration is used for sensor-level prelaunch. It will be used for stream-level prelaunch in a later version.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## activeTime

```TypeScript
activeTime?: number
```

Activation time, in minutes.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## cameraDevice

```TypeScript
cameraDevice: CameraDevice
```

Camera device.

**Type:** [CameraDevice](arkts-camera-camera-cameradevice-i.md)

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## restoreParamType

```TypeScript
restoreParamType?: RestoreParamType
```

Type of the parameter used for prelaunch.

**Type:** [RestoreParamType](arkts-camera-camera-restoreparamtype-e-sys.md)

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## settingParam

```TypeScript
settingParam?: SettingParam
```

Setting parameter.

**Type:** [SettingParam](arkts-camera-camera-settingparam-i-sys.md)

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.
