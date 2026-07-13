# AVRecorderProfile

Describes the audio and video recording profile.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## aacProfile

```TypeScript
aacProfile?: AacProfile
```

AAC profile for AAC audio encoder. If not set, use AAC_LC profile as default.

**类型：** AacProfile

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioBitrate

```TypeScript
audioBitrate?: number
```

Audio encoding bit rate, in bit/s. This parameter is mandatory for audio recording.<br>Supported bit rate ranges:
<br>- Range [32000 - 500000] for the AAC encoding format.<br>- Range [64000] for the G.711 μ-law encoding format.
<br>- Range [8000, 16000, 32000, 40000, 48000, 56000, 64000, 80000, 96000, 112000, 128000, 160000, 192000,
224000, 256000, 320000] for the MP3 encoding format.<br>When the MP3 encoding format is used,
the mapping between the sampling rate and bit rate is as follows:<br>- When the sampling rate is lower than
16 kHZ, the bit rate range is [8000 - 64000].<br>- When the sampling rate ranges from 16 kHz to 32 kHz,
the bit rate range is [8000 - 160000].<br>- When the sampling rate is greater than 32 kHz, the bit rate range
is [32000 - 320000].<br>- Range [4750, 5150, 5900, 6700, 7400, 7950, 10200, 12200] for
the AMR-NB encoding format.<br>- Range [6600, 8850, 12650, 14250, 15850, 18250, 19850, 23050, 23850] for the
AMR-WB encoding format.<br>**Atomic service API**: This API can be used in atomic services since API version 12.

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioChannels

```TypeScript
audioChannels?: number
```

Number of audio channels. This parameter is mandatory for audio recording.<br>- Range [1 - 8] for the
AAC encoding format.<br>- Range [1] for the G.711 μ-law encoding format.<br>- Range [1 - 2] for the MP3 encoding
format.<br>- Range [1] for the AMR-NB and AMR-WB encoding formats.<br>**Atomic service API**: This API can be
used in atomic services since API version 12.

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioCodec

```TypeScript
audioCodec?: CodecMimeType
```

Audio encoding format. This parameter is mandatory for audio recording. Currently, AUDIO_AAC, AUDIO_MP3,
AUDIO_G711MU, AUDIO_AMR_NB, and AUDIO_AMR_WB are supported.<br>**Atomic service API**: This API can be used in
atomic services since API version 12.

**类型：** CodecMimeType

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioSampleRate

```TypeScript
audioSampleRate?: number
```

Audio sampling rate, in Hz. This parameter is mandatory for audio recording.<br>Supported sampling rate ranges:
<br>- Range [8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000, 64000, 88200, 96000] for the AAC
encoding format.<br>- Range [8000] for the G.711 μ-law encoding format.<br>- Range [8000, 11025, 12000, 16000,
22050, 24000, 32000, 44100, 48000] for the MP3 encoding format.<br>- Range [8000] for the AMR-NB encoding format.
<br>- Range [16000] for the AMR-WB encoding format.<br>Variable bit rate. The bit rate is for reference only.
<br>**Atomic service API**: This API can be used in atomic services since API version 12.

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## enableBFrame

```TypeScript
enableBFrame?: boolean
```

Indicates whether enable B Frame. Default is disabled.

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## enableTemporalScale

```TypeScript
enableTemporalScale?: boolean
```

Whether temporal layered encoding is supported. This parameter is optional for video recording. The default value
is **false**. If this parameter is set to **true**, some frames in the video output streams can be skipped
without being encoded.

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## fileFormat

```TypeScript
fileFormat: ContainerFormatType
```

Container format of a file. This parameter is mandatory. Currently, the MP4, M4A, MP3, WAV, and AMR container
formats are supported. The AUDIO_MP3 encoding format cannot be used in the MP4 container format.<br>**Atomic
service API**: This API can be used in atomic services since API version 12.

**类型：** ContainerFormatType

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## isHdr

```TypeScript
isHdr?: boolean
```

HDR encoding. This parameter is optional for video recording. The default value is **false**, and there is no
requirement on the encoding format. When **isHdr** is set to **true**, the encoding format must be **video/hevc**
.

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoBitrate

```TypeScript
videoBitrate?: number
```

Video encoding bit rate, in bit/s. This parameter is mandatory for video recording. The value range is
[10000 - 100000000], in bit/s.

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoCodec

```TypeScript
videoCodec?: CodecMimeType
```

Video encoding format. This parameter is mandatory for video recording. Currently, VIDEO_AVC is supported.

**类型：** CodecMimeType

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoFrameHeight

```TypeScript
videoFrameHeight?: number
```

Height of a video frame, in px. This parameter is mandatory for video recording. The value range is [144 - 4096].

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoFrameRate

```TypeScript
videoFrameRate?: number
```

Video frame rate, in fps. This parameter is mandatory for video recording. The value range is [1 - 60].

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoFrameWidth

```TypeScript
videoFrameWidth?: number
```

Width of a video frame, in px. This parameter is mandatory for video recording. The value range is [176 - 4096].

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

