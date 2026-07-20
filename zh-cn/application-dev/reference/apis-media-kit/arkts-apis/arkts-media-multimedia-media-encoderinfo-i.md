# EncoderInfo

编码器信息描述。

**起始版本：** 11

<!--Device-unnamed-interface EncoderInfo--><!--Device-unnamed-interface EncoderInfo-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## bitRate

```TypeScript
bitRate?: Range
```

编码器比特率范围，包含最小和最大比特率，单位为bit/s。

**类型：** Range

**起始版本：** 11

<!--Device-EncoderInfo-bitRate?: Range--><!--Device-EncoderInfo-bitRate?: Range-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## channels

```TypeScript
channels?: Range
```

音频采集器的声道数范围，包含最小和最大声道数。仅在音频编码器中可用。

**类型：** Range

**起始版本：** 11

<!--Device-EncoderInfo-channels?: Range--><!--Device-EncoderInfo-channels?: Range-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## frameRate

```TypeScript
frameRate?: Range
```

视频帧率范围，包含最小和最大帧率，单位为fps。仅在视频编码器中可用。

**类型：** Range

**起始版本：** 11

<!--Device-EncoderInfo-frameRate?: Range--><!--Device-EncoderInfo-frameRate?: Range-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## height

```TypeScript
height?: Range
```

视频帧高度范围，包含最小和最大高度，单位为像素（px）。仅在视频编码器中可用。

**类型：** Range

**起始版本：** 11

<!--Device-EncoderInfo-height?: Range--><!--Device-EncoderInfo-height?: Range-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## mimeType

```TypeScript
mimeType: CodecMimeType
```

编码器的MIME类型。

**类型：** CodecMimeType

**起始版本：** 11

<!--Device-EncoderInfo-mimeType: CodecMimeType--><!--Device-EncoderInfo-mimeType: CodecMimeType-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## sampleRate

```TypeScript
sampleRate?: Array<number>
```

音频采样率，包含所有可用的音频采样率，单位为Hz。仅在音频编码器中可用。

**类型：** Array&lt;number&gt;

**起始版本：** 11

<!--Device-EncoderInfo-sampleRate?: Array<int>--><!--Device-EncoderInfo-sampleRate?: Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## type

```TypeScript
type: string
```

编码器类型。值audio表示音频编码器，值video表示视频编码器。

**类型：** string

**起始版本：** 11

<!--Device-EncoderInfo-type: string--><!--Device-EncoderInfo-type: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## width

```TypeScript
width?: Range
```

视频帧宽度范围，包含最小和最大宽度，单位为像素（px）。仅在视频编码器中可用。

**类型：** Range

**起始版本：** 11

<!--Device-EncoderInfo-width?: Range--><!--Device-EncoderInfo-width?: Range-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

