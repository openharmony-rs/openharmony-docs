# AVRecorderProfile

音视频录制配置参数。

**起始版本：** 9

<!--Device-unnamed-interface AVRecorderProfile--><!--Device-unnamed-interface AVRecorderProfile-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## aacProfile

```TypeScript
aacProfile?: AacProfile
```

AAC音频编码器的AAC profile。如果不设置，默认使用AAC_LC profile。

**类型：** AacProfile

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorderProfile-aacProfile?: AacProfile--><!--Device-AVRecorderProfile-aacProfile?: AacProfile-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioBitrate

```TypeScript
audioBitrate?: number
```

音频编码比特率，单位为bit/s。录制音频时该参数为必填参数。<br>支持的比特率范围：<br>- AAC编码格式范围 [32000 - 500000]。<br>- G.711 μ-law编码格式范围 [64000]。<br>- MP3编码格式范围 [8000, 16000, 32000, 40000, 48000, 56000, 64000, 80000, 96000, 112000, 128000, 160000, 192000,224000, 256000, 320000]。<br>使用MP3编码格式时，采样率和比特率的对应关系如下：<br>- 采样率低于16 kHz时，比特率范围为 [8000 - 64000]。<br>- 采样率在16 kHz至32 kHz之间时，比特率范围为 [8000 - 160000]。<br>- 采样率大于32 kHz时，比特率范围为 [32000 - 320000]。<br>- AMR-NB编码格式范围 [4750, 5150, 5900, 6700, 7400, 7950, 10200, 12200]。<br>- AMR-WB编码格式范围 [6600, 8850, 12650, 14250, 15850, 18250, 19850, 23050, 23850]。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorderProfile-audioBitrate?: int--><!--Device-AVRecorderProfile-audioBitrate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioChannels

```TypeScript
audioChannels?: number
```

音频声道数。录制音频时该参数为必填参数。<br>- AAC编码格式范围 [1 - 2]。<br>- G.711 μ-law编码格式范围 [1]。<br>- MP3编码格式范围 [1 - 2]。<br>- AMR-NB和AMR-WB编码格式范围 [1]。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorderProfile-audioChannels?: int--><!--Device-AVRecorderProfile-audioChannels?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioCodec

```TypeScript
audioCodec?: CodecMimeType
```

音频编码格式。录制音频时该参数为必填参数。当前支持AUDIO_AAC、AUDIO_MP3、AUDIO_G711MU、AUDIO_AMR_NB和AUDIO_AMR_WB。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**类型：** CodecMimeType

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorderProfile-audioCodec?: CodecMimeType--><!--Device-AVRecorderProfile-audioCodec?: CodecMimeType-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioSampleRate

```TypeScript
audioSampleRate?: number
```

音频采样率，单位为Hz。录制音频时该参数为必填参数。<br>支持的采样率范围：<br>- AAC编码格式范围 [8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000, 64000, 88200, 96000]。<br>- G.711 μ-law编码格式范围 [8000]。<br>- MP3编码格式范围 [8000, 11025, 12000, 16000,22050, 24000, 32000, 44100, 48000]。<br>- AMR-NB编码格式范围 [8000]。<br>- AMR-WB编码格式范围 [16000]。<br>可变比特率。比特率仅供参考。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorderProfile-audioSampleRate?: int--><!--Device-AVRecorderProfile-audioSampleRate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## enableBFrame

```TypeScript
enableBFrame?: boolean
```

是否启用B帧。默认不启用。

**类型：** boolean

**起始版本：** 20

<!--Device-AVRecorderProfile-enableBFrame?: boolean--><!--Device-AVRecorderProfile-enableBFrame?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## enableTemporalScale

```TypeScript
enableTemporalScale?: boolean
```

是否支持时域分层编码。录制视频时该参数可选。默认值为**false**。如果设置为**true**，视频输出流中的部分帧可以跳过不编码。

**类型：** boolean

**起始版本：** 12

<!--Device-AVRecorderProfile-enableTemporalScale?: boolean--><!--Device-AVRecorderProfile-enableTemporalScale?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## fileFormat

```TypeScript
fileFormat: ContainerFormatType
```

文件的容器格式。此参数为必填参数。当前支持MP4、M4A、MP3、WAV、AMR和AAC容器格式。AUDIO_MP3编码格式不能在MP4容器格式中使用。<br>**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**类型：** ContainerFormatType

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorderProfile-fileFormat: ContainerFormatType--><!--Device-AVRecorderProfile-fileFormat: ContainerFormatType-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## isHdr

```TypeScript
isHdr?: boolean
```

HDR编码。录制视频时该参数可选。默认值为**false**，对编码格式无要求。当**isHdr**设置为**true**时，编码格式必须为**video/hevc**。

**类型：** boolean

**起始版本：** 11

<!--Device-AVRecorderProfile-isHdr?: boolean--><!--Device-AVRecorderProfile-isHdr?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoBitrate

```TypeScript
videoBitrate?: number
```

视频编码比特率，单位为bit/s。录制视频时该参数为必填参数。取值范围为[10000 - 100000000]。

**类型：** number

**起始版本：** 9

<!--Device-AVRecorderProfile-videoBitrate?: int--><!--Device-AVRecorderProfile-videoBitrate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoCodec

```TypeScript
videoCodec?: CodecMimeType
```

视频编码格式。录制视频时该参数为必填参数。当前支持VIDEO_AVC和VIDEO_HEVC。

**类型：** CodecMimeType

**起始版本：** 9

<!--Device-AVRecorderProfile-videoCodec?: CodecMimeType--><!--Device-AVRecorderProfile-videoCodec?: CodecMimeType-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoFrameHeight

```TypeScript
videoFrameHeight?: number
```

视频帧高度，单位为像素（px）。录制视频时该参数为必填参数。取值范围为[144 - 4096]。

**类型：** number

**起始版本：** 9

<!--Device-AVRecorderProfile-videoFrameHeight?: int--><!--Device-AVRecorderProfile-videoFrameHeight?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoFrameRate

```TypeScript
videoFrameRate?: number
```

视频帧率，单位为fps。录制视频时该参数为必填参数。取值范围为[1 - 60]。

**类型：** number

**起始版本：** 9

<!--Device-AVRecorderProfile-videoFrameRate?: int--><!--Device-AVRecorderProfile-videoFrameRate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoFrameWidth

```TypeScript
videoFrameWidth?: number
```

视频帧宽度，单位为像素（px）。录制视频时该参数为必填参数。取值范围为[176 - 4096]。

**类型：** number

**起始版本：** 9

<!--Device-AVRecorderProfile-videoFrameWidth?: int--><!--Device-AVRecorderProfile-videoFrameWidth?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

