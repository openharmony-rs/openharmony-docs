# AudioPlaybackCaptureMode

表示内录（录制设备内部应用的声音）模式的枚举。不同模式决定可录制的目标播放流类型。支持通过按位或组合枚举值，当前仅支持MODE_DEFAULT（0x0）、MODE_MEDIA（0x1）、MODE_EXCLUDING_SELF（0x
8000），以及MODE_MEDIA和MODE_EXCLUDING_SELF的按位或组合（0x8001）。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## MODE_DEFAULT

```TypeScript
MODE_DEFAULT = 0x0
```

默认模式。录制大部分音频流，但不包括提示音流和隐私流。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## MODE_MEDIA

```TypeScript
MODE_MEDIA = 0x1
```

媒体模式。录制媒体、语音消息和未知类型的音频流。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## MODE_EXCLUDING_SELF

```TypeScript
MODE_EXCLUDING_SELF = 0x8000
```

排除自身模式。录制除应用自身播放的音频以外的音频流。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

