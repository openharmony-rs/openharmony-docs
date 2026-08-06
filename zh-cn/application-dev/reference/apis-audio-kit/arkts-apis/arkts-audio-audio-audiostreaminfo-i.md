# AudioStreamInfo

音频流信息。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-audio-interface AudioStreamInfo--><!--Device-audio-interface AudioStreamInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## channelLayout

```TypeScript
channelLayout?: AudioChannelLayout
```

音频声道布局，默认值为0x0。

**类型：** AudioChannelLayout

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-AudioStreamInfo-channelLayout?: AudioChannelLayout--><!--Device-AudioStreamInfo-channelLayout?: AudioChannelLayout-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## channels

```TypeScript
channels: AudioChannel
```

音频文件的通道数。

**类型：** AudioChannel

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-AudioStreamInfo-channels: AudioChannel--><!--Device-AudioStreamInfo-channels: AudioChannel-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## encodingType

```TypeScript
encodingType: AudioEncodingType
```

音频编码格式。

**类型：** AudioEncodingType

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-AudioStreamInfo-encodingType: AudioEncodingType--><!--Device-AudioStreamInfo-encodingType: AudioEncodingType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## sampleFormat

```TypeScript
sampleFormat: AudioSampleFormat
```

音频采样格式。

**类型：** AudioSampleFormat

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-AudioStreamInfo-sampleFormat: AudioSampleFormat--><!--Device-AudioStreamInfo-sampleFormat: AudioSampleFormat-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## samplingRate

```TypeScript
samplingRate: AudioSamplingRate | int
```

音频文件的采样率，单位为赫兹（Hz）。支持传入[AudioSamplingRate]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 从API版本26.0.0开始： - 参数samplingRate支持number类型。 - 音频渲染扩展支持8000Hz到384000Hz范围内以10Hz为步长的采样率值。具体设备支持的采样率规格会存在差异。

**类型：** AudioSamplingRate \| int

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

**模型约束：** 
- API版本26.0.0+：此接口可在Stage模型和FA模型下使用。

<!--Device-AudioStreamInfo-samplingRate: AudioSamplingRate | int--><!--Device-AudioStreamInfo-samplingRate: AudioSamplingRate | int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

