# TorchStatusInfo

手电筒回调返回的接口实例，表示手电筒状态信息。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## isTorchActive

```TypeScript
readonly isTorchActive: boolean
```

手电筒是否被激活。true表示手电筒被激活，false表示手电筒未被激活。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isTorchAvailable

```TypeScript
readonly isTorchAvailable: boolean
```

手电筒是否可用。true表示手电筒可用，false表示手电筒不可用。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## torchLevel

```TypeScript
readonly torchLevel: number
```

手电筒亮度等级，取值范围为[0,1]，越靠近1，亮度越大。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core
