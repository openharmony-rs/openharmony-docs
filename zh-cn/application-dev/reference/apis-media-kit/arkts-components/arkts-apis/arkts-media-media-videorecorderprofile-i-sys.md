# VideoRecorderProfile（系统接口）

视频录制的配置文件。

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

音频编码比特率，选择音频录制时必填。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## audioChannels

```TypeScript
readonly audioChannels: number
```

音频采集声道数，选择音频录制时必填。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## audioCodec

```TypeScript
readonly audioCodec: CodecMimeType
```

音频编码格式，选择音频录制时必填。

**类型：** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## audioSampleRate

```TypeScript
readonly audioSampleRate: number
```

音频采样率，选择音频录制时必填。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## fileFormat

```TypeScript
readonly fileFormat: ContainerFormatType
```

文件的容器格式。

**类型：** [ContainerFormatType](arkts-media-media-containerformattype-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## videoBitrate

```TypeScript
readonly videoBitrate: number
```

视频编码比特率。

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

录制视频帧的高。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## videoFrameRate

```TypeScript
readonly videoFrameRate: number
```

录制视频帧率。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## videoFrameWidth

```TypeScript
readonly videoFrameWidth: number
```

录制视频帧的宽。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。
