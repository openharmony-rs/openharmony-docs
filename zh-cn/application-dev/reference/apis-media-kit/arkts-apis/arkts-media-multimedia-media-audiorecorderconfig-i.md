# AudioRecorderConfig

音频录制配置定义。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** AVRecorderConfig

<!--Device-unnamed-interface AudioRecorderConfig--><!--Device-unnamed-interface AudioRecorderConfig-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## audioEncodeBitRate

```TypeScript
audioEncodeBitRate?: number
```

音频编码比特率，单位为bit/s。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** audioBitrate

<!--Device-AudioRecorderConfig-audioEncodeBitRate?: number--><!--Device-AudioRecorderConfig-audioEncodeBitRate?: number-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## audioEncoder

```TypeScript
audioEncoder?: AudioEncoder
```

音频编码格式。默认值为DEFAULT，API8之后将废弃。请使用"audioEncoderMime"替代。

**类型：** AudioEncoder

**起始版本：** 6

**废弃版本：** 8

**替代接口：** audioEncoderMime

<!--Device-AudioRecorderConfig-audioEncoder?: AudioEncoder--><!--Device-AudioRecorderConfig-audioEncoder?: AudioEncoder-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## audioEncoderMime

```TypeScript
audioEncoderMime?: CodecMimeType
```

音频编码格式MIME。用于替代audioEncoder。

**类型：** CodecMimeType

**起始版本：** 8

**废弃版本：** 9

**替代接口：** audioCodec

<!--Device-AudioRecorderConfig-audioEncoderMime?: CodecMimeType--><!--Device-AudioRecorderConfig-audioEncoderMime?: CodecMimeType-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## audioSampleRate

```TypeScript
audioSampleRate?: number
```

音频采样率，单位为Hz。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** audioSampleRate

<!--Device-AudioRecorderConfig-audioSampleRate?: number--><!--Device-AudioRecorderConfig-audioSampleRate?: number-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## fileFormat

```TypeScript
fileFormat?: ContainerFormatType
```

输出文件格式，详见ContainerFormatType。用于替代"format"。

**类型：** ContainerFormatType

**起始版本：** 8

**废弃版本：** 9

**替代接口：** fileFormat

<!--Device-AudioRecorderConfig-fileFormat?: ContainerFormatType--><!--Device-AudioRecorderConfig-fileFormat?: ContainerFormatType-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## format

```TypeScript
format?: AudioOutputFormat
```

音频输出格式。默认值为DEFAULT。API8之后废弃，使用"fileFormat"替代。

**类型：** AudioOutputFormat

**起始版本：** 6

**废弃版本：** 8

**替代接口：** fileFormat

<!--Device-AudioRecorderConfig-format?: AudioOutputFormat--><!--Device-AudioRecorderConfig-format?: AudioOutputFormat-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## location

```TypeScript
location?: Location
```

地理位置信息。

**类型：** Location

**起始版本：** 6

**废弃版本：** 9

**替代接口：** location

<!--Device-AudioRecorderConfig-location?: Location--><!--Device-AudioRecorderConfig-location?: Location-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## numberOfChannels

```TypeScript
numberOfChannels?: number
```

音频声道数。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** audioChannels

<!--Device-AudioRecorderConfig-numberOfChannels?: number--><!--Device-AudioRecorderConfig-numberOfChannels?: number-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## uri

```TypeScript
uri: string
```

音频输出URI。支持两种URI格式。格式：scheme + "://" + "context"。file格式：file://path fd格式：fd://fd

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** url

<!--Device-AudioRecorderConfig-uri: string--><!--Device-AudioRecorderConfig-uri: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

