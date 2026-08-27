# AVRecorderProfile

音视频录制配置参数。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## aacProfile

```TypeScript
aacProfile?: AacProfile
```

音频编码扩展格式，默认为AAC_LC格式。当前支持类型：AAC_LC、AAC_HE和AAC_HE_V2。  
 **原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**类型：** [AacProfile](arkts-media-media-aacprofile-e.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioBitrate

```TypeScript
audioBitrate?: number
```

音频编码比特率，选择音频录制时必填。单位为比特/秒（bit/s）。取值范围：

- AAC编码格式支持比特率范围[32000, 500000]。

- G711-mulaw编码格式支持比特率大小：64000。

- MP3编码格式取值范围[8000, 16000, 32000, 40000, 48000, 56000, 64000, 80000, 96000, 112000, 128000, 160000, 192000,  
224000, 256000, 320000]。当使用MP3编码格式时，采样率和比特率的映射关系：

- 采样率使用16K以下时，对应比特率范围为[8000 - 64000]。

- 采样率使用16K~32K时对应的比特率范围为[8000, 160000]。

- 采样率使用32K以上时对应的比特率范围为[32000, 320000]。

- AMR_NB编码格式支持比特率范围[4750, 5150, 5900, 6700, 7400, 7950, 10200, 12200]。

- AMR_WB编码格式支持比特率范围[6600, 8850, 12650, 14250, 15850, 18250, 19850, 23050, 23850]。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioChannels

```TypeScript
audioChannels?: number
```

音频采集声道数，选择音频录制时必填。

- AAC编码格式取值范围[1, 2]。

- G711-mulaw编码格式支持大小：1。

- MP3编码格式取值范围[1, 2]。

- AMR-NB和AMR-WB编码格式支持大小：1。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioCodec

```TypeScript
audioCodec?: CodecMimeType
```

音频编码格式，选择音频录制时必填。当前支持AUDIO_AAC、AUDIO_MP3、AUDIO_G711MU、AUDIO_AMR_NB和AUDIO_AMR_WB。  
 **原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioSampleRate

```TypeScript
audioSampleRate?: number
```

音频采样率，选择音频录制时必填。单位为赫兹（Hz）。取值范围：

- AAC编码支持采样率范围[8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000, 64000, 88200, 96000]。

- G711-mulaw编码支持采样率大小：8000。

- MP3编码支持采样率范围[8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000]。

- AMR_NB编码支持采样率大小：8000。

- AMR_WB编码支持采样率大小：16000。

可变比特率模式，码率仅作参考。  
 **原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## enableBFrame

```TypeScript
enableBFrame?: boolean
```

视频录制是否启用B帧编码。true表示启用B帧编码（仅在视频编码格式为H.265且设备硬件支持的情况下生效），false表示不启用B帧编码。该参数为视频录制场景下的可选项，默认值为false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## enableTemporalScale

```TypeScript
enableTemporalScale?: boolean
```

视频录制是否支持时域分层编码功能，选择视频录制时选填，enableTemporalScale默认为false。设置为true时，编码输出的码流中部分帧可以支持跳过不编码。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## fileFormat

```TypeScript
fileFormat: ContainerFormatType
```

文件的容器格式，必要参数。当前支持MP4、M4A、MP3、WAV、AMR、AAC封装格式，当前AAC音频封装默认为ADTS帧头格式。不支持在MP4封装格式下使用AUDIO_MP3编码格式。  
 **原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [ContainerFormatType](arkts-media-media-containerformattype-e.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## isHdr

```TypeScript
isHdr?: boolean
```

HDR编码，选择视频录制时选填。isHdr默认为false，对应编码格式没有要求，isHdr为true时，对应的编码格式必须为video/hevc。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoBitrate

```TypeScript
videoBitrate?: number
```

视频编码比特率，选择视频录制时必填。取值范围[10000, 100000000]，单位为比特/秒（bit/s）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoCodec

```TypeScript
videoCodec?: CodecMimeType
```

视频编码格式，选择视频录制时必填。当前支持VIDEO_AVC和VIDEO_HEVC。

**类型：** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoFrameHeight

```TypeScript
videoFrameHeight?: number
```

视频帧的高，选择视频录制时必填。取值范围[144, 4096]，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoFrameRate

```TypeScript
videoFrameRate?: number
```

视频帧率，选择视频录制时必填。推荐范围[1, 60]，单位为帧/秒（fps）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoFrameWidth

```TypeScript
videoFrameWidth?: number
```

视频帧的宽，选择视频录制时必填。取值范围[176, 4096]，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder
