# CameraConcurrentInfo

相机的输出并发能力信息。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## device

```TypeScript
readonly device: CameraDevice
```

相机并发设备。

**类型：** [CameraDevice](arkts-camera-camera-cameradevice-i.md)

**起始版本：** 18

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## modes

```TypeScript
readonly modes: Array<SceneMode>
```

相机支持的模式。

**类型：** Array&lt;[SceneMode](arkts-camera-camera-scenemode-e.md)&gt;

**起始版本：** 18

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## outputCapabilities

```TypeScript
readonly outputCapabilities: Array<CameraOutputCapability>
```

相机对应模式的输出能力集。

**类型：** Array&lt;[CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md)&gt;

**起始版本：** 18

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## type

```TypeScript
readonly type: CameraConcurrentType
```

镜头并发类型。

**类型：** [CameraConcurrentType](arkts-camera-camera-cameraconcurrenttype-e.md)

**起始版本：** 18

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core
