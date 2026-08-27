# AudioStreamInfo

音频流信息。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Core

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## channelLayout

```TypeScript
channelLayout?: AudioChannelLayout
```

音频声道布局，默认值为0x0。

**类型：** [AudioChannelLayout](arkts-audio-audio-audiochannellayout-e.md)

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Core

## channels

```TypeScript
channels: AudioChannel
```

音频文件的通道数。

**类型：** [AudioChannel](arkts-audio-audio-audiochannel-e.md)

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Core

## encodingType

```TypeScript
encodingType: AudioEncodingType
```

音频编码格式。

**类型：** [AudioEncodingType](arkts-audio-audio-audioencodingtype-e.md)

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Core

## sampleFormat

```TypeScript
sampleFormat: AudioSampleFormat
```

音频采样格式。

**类型：** [AudioSampleFormat](arkts-audio-audio-audiosampleformat-e.md)

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Core

## samplingRate

```TypeScript
samplingRate: AudioSamplingRate | number
```

音频文件的采样率，单位为赫兹（Hz）。支持传入[AudioSamplingRate](arkts-audio-audio-audiosamplingrate-e.md)。从API版本26.0.0开始：  
- 参数samplingRate支持number类型。  
- 音频渲染扩展支持8000Hz到384000Hz范围内以10Hz为步长的采样率值。具体设备支持的采样率规格会存在差异。

**类型：** [AudioSamplingRate](arkts-audio-audio-audiosamplingrate-e.md) \| number

**起始版本：** 8

**模型约束：** 
- API版本26.0.0+：此接口可在Stage模型和FA模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core
