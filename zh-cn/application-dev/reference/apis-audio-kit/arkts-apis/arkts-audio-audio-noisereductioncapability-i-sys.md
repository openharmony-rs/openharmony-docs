# NoiseReductionCapability（系统接口）

支持降噪能力的外部音频设备信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## device

```TypeScript
device: AudioDeviceDescriptor
```

外部音频设备信息。

**类型：** [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## supportedModes

```TypeScript
supportedModes: Array<NoiseReductionMode>
```

外部设备支持的降噪模式。

**类型：** Array&lt;[NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。
