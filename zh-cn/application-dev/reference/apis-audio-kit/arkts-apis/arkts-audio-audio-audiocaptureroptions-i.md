# AudioCapturerOptions

音频采集器选项信息。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## capturerInfo

```TypeScript
capturerInfo: AudioCapturerInfo
```

音频采集器信息。SystemCapability.Multimedia.Audio.Capturer

**类型：** [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md)

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## playbackCaptureConfig

```TypeScript
playbackCaptureConfig?: AudioPlaybackCaptureConfig
```

音频内录的配置信息。SystemCapability.Multimedia.Audio.PlaybackCapture从API version 10开始支持，从API version 12开始废弃，建议使用[录屏接口AVScreenCapture](../apis-media-kit/capi-avscreencapture.md)替代。

**类型：** [AudioPlaybackCaptureConfig](arkts-audio-audio-audioplaybackcaptureconfig-i.md)

**起始版本：** 10

**废弃版本：** 12

**替代接口：** OH_AVScreenCapture

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## playbackCaptureMode

```TypeScript
playbackCaptureMode?: AudioPlaybackCaptureMode
```

内录模式。可设置为AudioPlaybackCaptureMode中的枚举值或其按位或组合，当前仅支持MODE_DEFAULT（0x0）、MODE_MEDIA（0x1）、MODE_EXCLUDING_SELF（0x8000）， 以及MODE_MEDIA和MODE_EXCLUDING_SELF的按位或组合（0x8001）。
26.0.0
此接口仅可在Stage模型下使用。SystemCapability.Multimedia.Audio.PlaybackCapture

**类型：** [AudioPlaybackCaptureMode](arkts-audio-audio-audioplaybackcapturemode-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## streamInfo

```TypeScript
streamInfo: AudioStreamInfo
```

音频流信息。SystemCapability.Multimedia.Audio.Capturer

**类型：** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Capturer
