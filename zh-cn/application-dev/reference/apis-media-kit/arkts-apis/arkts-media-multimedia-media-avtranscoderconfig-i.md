# AVTranscoderConfig

Describes the video transcoding parameters.

**起始版本：** 12

<!--Device-unnamed-interface AVTranscoderConfig--><!--Device-unnamed-interface AVTranscoderConfig-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## audioBitrate

```TypeScript
audioBitrate?: number
```

Bitrate of the output audio, in bit/s. The value range is [1-500000]. The default value is 48 kbit/s.

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoderConfig-audioBitrate?: int--><!--Device-AVTranscoderConfig-audioBitrate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## audioCodec

```TypeScript
audioCodec?: CodecMimeType
```

Encoding format of the output audio. Currently, only AAC is supported. The default value is **AAC**.

**类型：** CodecMimeType

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoderConfig-audioCodec?: CodecMimeType--><!--Device-AVTranscoderConfig-audioCodec?: CodecMimeType-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## enableBFrame

```TypeScript
enableBFrame?: boolean
```

Indicates whether to enable B Frame Encoding for reduce file size.

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoderConfig-enableBFrame?: boolean--><!--Device-AVTranscoderConfig-enableBFrame?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## fileFormat

```TypeScript
fileFormat: ContainerFormatType
```

Container format of the output video file. Currently, only MP4 is supported.

**类型：** ContainerFormatType

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoderConfig-fileFormat: ContainerFormatType--><!--Device-AVTranscoderConfig-fileFormat: ContainerFormatType-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## videoBitrate

```TypeScript
videoBitrate?: number
```

Bitrate of the output video, in bit/s. The default bitrate depends on the resolution of the output video.The default bitrate is 1 Mbit/s for the resolution in the range [240p, 480P],2 Mbit/s for the range (480P,720P], 4 Mbit/s for the range (720P,1080P], and 8 Mbit/s for 1080p or higher.

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoderConfig-videoBitrate?: int--><!--Device-AVTranscoderConfig-videoBitrate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## videoCodec

```TypeScript
videoCodec?: CodecMimeType
```

Encoding format of the output video. Currently, only AVC and HEVC are supported.If the source video is in HEVC format, the default value is **HEVC**. Otherwise, the default value is **AVC**.

**类型：** CodecMimeType

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoderConfig-videoCodec?: CodecMimeType--><!--Device-AVTranscoderConfig-videoCodec?: CodecMimeType-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## videoFrameHeight

```TypeScript
videoFrameHeight?: number
```

Height of the output video frame, in px. The value range is [240 - 2160].The default value is the height of the source video frame.

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoderConfig-videoFrameHeight?: int--><!--Device-AVTranscoderConfig-videoFrameHeight?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## videoFrameWidth

```TypeScript
videoFrameWidth?: number
```

Width of the output video frame, in px. The value range is [240 - 3840].The default value is the width of the source video frame.

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoderConfig-videoFrameWidth?: int--><!--Device-AVTranscoderConfig-videoFrameWidth?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

