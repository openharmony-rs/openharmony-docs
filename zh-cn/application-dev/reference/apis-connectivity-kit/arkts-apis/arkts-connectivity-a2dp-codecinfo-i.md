# CodecInfo

蓝牙媒体音频使用的编解码器。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { a2dp } from '@kit.ConnectivityKit';
```

## codecBitRate

```TypeScript
codecBitRate?: CodecBitRate
```

编解码器的码率，默认值为CODEC_BIT_RATE_ABR。

**类型：** [CodecBitRate](arkts-connectivity-a2dp-codecbitrate-e.md)

**起始版本：** 19

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## codecBitsPerSample

```TypeScript
codecBitsPerSample: CodecBitsPerSample
```

每个采样点的位深，默认值为CODEC_BITS_PER_SAMPLE_NONE。

**类型：** [CodecBitsPerSample](arkts-connectivity-a2dp-codecbitspersample-e.md)

**起始版本：** 11

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## codecChannelMode

```TypeScript
codecChannelMode: CodecChannelMode
```

编解码器的声道模式，默认值为CODEC_CHANNEL_MODE_NONE。

**类型：** [CodecChannelMode](arkts-connectivity-a2dp-codecchannelmode-e.md)

**起始版本：** 11

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## codecFrameLength

```TypeScript
codecFrameLength?: CodecFrameLength
```

编解码器的帧长，默认值为CODEC_FRAME_LENGTH_10MS。

**类型：** [CodecFrameLength](arkts-connectivity-a2dp-codecframelength-e.md)

**起始版本：** 19

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## codecSampleRate

```TypeScript
codecSampleRate: CodecSampleRate
```

编解码器的采样率，默认值为CODEC_SAMPLE_RATE_NONE。

**类型：** [CodecSampleRate](arkts-connectivity-a2dp-codecsamplerate-e.md)

**起始版本：** 11

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## codecType

```TypeScript
codecType: CodecType
```

编解码器类型，默认值为CODEC_TYPE_SBC。

**类型：** [CodecType](arkts-connectivity-a2dp-codectype-e.md)

**起始版本：** 11

**系统能力：** SystemCapability.Communication.Bluetooth.Core
