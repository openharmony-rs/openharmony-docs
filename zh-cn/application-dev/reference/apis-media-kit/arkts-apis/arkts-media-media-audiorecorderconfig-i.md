# AudioRecorderConfig


> **说明：**
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md)替代。
表示音频的录音配置。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## audioEncodeBitRate

```TypeScript
audioEncodeBitRate?: number
```

音频编码比特率，默认值为48000。单位为比特每秒（bit/s）。  
**说明：** 从API version 6开始支持，从API version 9开始废弃， 建议使用[AVRecorderProfile](arkts-media-media-avrecorderprofile-i.md)中的audioBitrate替代。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [audioBitrate](arkts-media-media-avrecorderprofile-i.md#audiobitrate)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## audioEncoder

```TypeScript
audioEncoder?: AudioEncoder
```

音频编码格式，默认设置为AAC_LC。  
**说明：** 从API version 6开始支持，从API version 8开始废弃，建议使用audioEncoderMime替代。

**类型：** [AudioEncoder](arkts-media-media-audioencoder-e.md)

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [audioEncoderMime](#audioencodermime)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## audioEncoderMime

```TypeScript
audioEncoderMime?: CodecMimeType
```

音频编码格式。  
**说明：** 从API version 8开始支持，从API version 9开始废弃， 建议使用[AVRecorderProfile](arkts-media-media-avrecorderprofile-i.md)中的audioCodec替代。

**类型：** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [audioCodec](arkts-media-media-avrecorderprofile-i.md#audiocodec)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## audioSampleRate

```TypeScript
audioSampleRate?: number
```

音频采集采样率，默认值为48000。单位为赫兹（Hz）。可变比特率模式，码率仅作参考。  
**说明：** 从API version 6开始支持，从API version 9开始废弃， 建议使用[AVRecorderProfile](arkts-media-media-avrecorderprofile-i.md)中的audioSampleRate替代。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [audioSampleRate](arkts-media-media-avrecorderprofile-i.md#audiosamplerate)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## fileFormat

```TypeScript
fileFormat?: ContainerFormatType
```

文件容器格式。  
**说明：** 从API version 8开始支持，从API version 9开始废弃， 建议使用[AVRecorderProfile](arkts-media-media-avrecorderprofile-i.md)中的fileFormat替代。

**类型：** [ContainerFormatType](arkts-media-media-containerformattype-e.md)

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [fileFormat](arkts-media-media-avrecorderprofile-i.md#fileformat)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## format

```TypeScript
format?: AudioOutputFormat
```

音频输出封装格式，默认设置为MPEG_4。  
**说明：** 从API version 6开始支持，从API version 8开始废弃，建议使用fileFormat替代。

**类型：** [AudioOutputFormat](arkts-media-media-audiooutputformat-e.md)

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [fileFormat](#fileformat)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## location

```TypeScript
location?: Location
```

音频采集的地理位置。  
**说明：** 从API version 6开始支持，从API version 9开始废弃，建议使用[AVMetadata](arkts-media-media-avmetadata-i.md)中的location替代。

**类型：** Location

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [location](arkts-media-media-avmetadata-i.md#location)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## numberOfChannels

```TypeScript
numberOfChannels?: number
```

音频采集声道数，默认值为2。  
**说明：** 从API version 6开始支持，从API version 9开始废弃， 建议使用[AVRecorderProfile](arkts-media-media-avrecorderprofile-i.md)中的audioChannels替代。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [audioChannels](arkts-media-media-avrecorderprofile-i.md#audiochannels)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder

## uri

```TypeScript
uri: string
```

音频输出URI：fd://xx (fd number)文件需要由调用者创建，并赋予适当的权限。  
**说明：** 从API version 6开始支持，从API version 9开始废弃，建议使用[AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md)中的url替代。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [url](arkts-media-media-avrecorderconfig-i.md#url)

**系统能力：** SystemCapability.Multimedia.Media.AudioRecorder
