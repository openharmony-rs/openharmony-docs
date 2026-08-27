# VideoRecorderProfile（系统接口）

视频录制配置参数定义。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## audioBitrate

```TypeScript
readonly audioBitrate: number
```

音频比特率，单位为bit/s。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## audioChannels

```TypeScript
readonly audioChannels: number
```

音频声道数。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## audioCodec

```TypeScript
readonly audioCodec: CodecMimeType
```

音频编码格式。

**类型：** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## audioSampleRate

```TypeScript
readonly audioSampleRate: number
```

音频采样率，单位为Hz。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## fileFormat

```TypeScript
readonly fileFormat: ContainerFormatType
```

输出文件格式。

**类型：** [ContainerFormatType](arkts-media-media-containerformattype-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## videoBitrate

```TypeScript
readonly videoBitrate: number
```

视频比特率，单位为bit/s。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## videoCodec

```TypeScript
readonly videoCodec: CodecMimeType
```

视频编码格式。

**类型：** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## videoFrameHeight

```TypeScript
readonly videoFrameHeight: number
```

视频高度，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## videoFrameRate

```TypeScript
readonly videoFrameRate: number
```

视频帧率，单位为fps。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## videoFrameWidth

```TypeScript
readonly videoFrameWidth: number
```

视频宽度，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。
