# NoiseReductionConfigAction（系统接口）

降噪配置操作。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## appName

```TypeScript
appName: string
```

用于配置降噪功能的应用程序名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## device

```TypeScript
device: AudioDeviceDescriptor
```

配置降噪功能的设备描述符。

**类型：** [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## noiseReductionMode

```TypeScript
noiseReductionMode: NoiseReductionMode
```

用于配置降噪的模式。

**类型：** [NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。
