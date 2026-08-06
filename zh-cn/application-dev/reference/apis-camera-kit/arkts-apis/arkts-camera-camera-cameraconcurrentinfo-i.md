# CameraConcurrentInfo

相机的输出并发能力信息。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-camera-interface CameraConcurrentInfo--><!--Device-camera-interface CameraConcurrentInfo-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## device

```TypeScript
readonly device: CameraDevice
```

相机并发设备。

**类型：** CameraDevice

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraConcurrentInfo-readonly device: CameraDevice--><!--Device-CameraConcurrentInfo-readonly device: CameraDevice-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## modes

```TypeScript
readonly modes: Array<SceneMode>
```

相机支持的模式。

**类型：** Array&lt;SceneMode&gt;

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraConcurrentInfo-readonly modes: Array<SceneMode>--><!--Device-CameraConcurrentInfo-readonly modes: Array<SceneMode>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## outputCapabilities

```TypeScript
readonly outputCapabilities: Array<CameraOutputCapability>
```

相机对应模式的输出能力集。

**类型：** Array&lt;CameraOutputCapability&gt;

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraConcurrentInfo-readonly outputCapabilities: Array<CameraOutputCapability>--><!--Device-CameraConcurrentInfo-readonly outputCapabilities: Array<CameraOutputCapability>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## type

```TypeScript
readonly type: CameraConcurrentType
```

镜头并发类型。

**类型：** CameraConcurrentType

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraConcurrentInfo-readonly type: CameraConcurrentType--><!--Device-CameraConcurrentInfo-readonly type: CameraConcurrentType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

