# TorchStatusInfo

手电筒回调返回的接口实例，表示手电筒状态信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface TorchStatusInfo--><!--Device-camera-interface TorchStatusInfo-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isTorchActive

```TypeScript
readonly isTorchActive: boolean
```

手电筒是否被激活。true表示手电筒被激活，false表示手电筒未被激活。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-TorchStatusInfo-readonly isTorchActive: boolean--><!--Device-TorchStatusInfo-readonly isTorchActive: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isTorchAvailable

```TypeScript
readonly isTorchAvailable: boolean
```

手电筒是否可用。true表示手电筒可用，false表示手电筒不可用。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-TorchStatusInfo-readonly isTorchAvailable: boolean--><!--Device-TorchStatusInfo-readonly isTorchAvailable: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## torchLevel

```TypeScript
readonly torchLevel: double
```

手电筒亮度等级，取值范围为[0,1]，越靠近1，亮度越大。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-TorchStatusInfo-readonly torchLevel: double--><!--Device-TorchStatusInfo-readonly torchLevel: double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

