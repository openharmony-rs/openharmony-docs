# AudioCapturerOptions

音频采集器选项信息。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## capturerInfo

```TypeScript
capturerInfo: AudioCapturerInfo
```

音频采集器信息。

**类型：** AudioCapturerInfo

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## playbackCaptureConfig

```TypeScript
playbackCaptureConfig?: AudioPlaybackCaptureConfig
```

音频内录的配置信息。

<br/

**类型：** AudioPlaybackCaptureConfig

**起始版本：** 10

**废弃版本：** 12

**替代接口：** OH_AVScreenCapture

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## playbackCaptureMode

```TypeScript
playbackCaptureMode?: AudioPlaybackCaptureMode
```

内录模式。可设置为AudioPlaybackCaptureMode中的枚举值或其按位或组合，当前仅支持MODE_DEFAULT（0x0）、MODE_MEDIA（0x1）、MODE_EXCLUDING_SELF（0x8000），
以及MODE_MEDIA和MODE_EXCLUDING_SELF的按位或组合（0x8001）。

**类型：** AudioPlaybackCaptureMode

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## streamInfo

```TypeScript
streamInfo: AudioStreamInfo
```

音频流信息。

**类型：** AudioStreamInfo

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

