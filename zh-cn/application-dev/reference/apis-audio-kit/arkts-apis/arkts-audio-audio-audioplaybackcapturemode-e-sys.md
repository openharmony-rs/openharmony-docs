# AudioPlaybackCaptureMode

```TypeScript
enum AudioPlaybackCaptureMode
```

表示内录（录制设备内部应用的声音）模式的枚举。不同模式决定可录制的目标播放流类型。支持通过按位或组合枚举值，当前仅支持MODE_DEFAULT（0x0）、MODE_MEDIA（0x1）、MODE_EXCLUDING_SELF（0x 8000），以及MODE_MEDIA和MODE_EXCLUDING_SELF的按位或组合（0x8001）。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## MODE_ONLY_VOIP

```TypeScript
MODE_ONLY_VOIP = 0x4000
```

VoIP模式。录制VoIP音频流。

如果设置了[AudioCapturerOptions](arkts-audio-audio-audiocaptureroptions-i.md).playbackCaptureUid，则仅录制指定应用的VoIP音频流。

AudioCapturerOptions.playbackCaptureUid仅在此模式生效。

此模式需要`ohos.permission.CAPTURE_VOICE_DOWNLINK_AUDIO`权限，否则[createAudioCapturer](./arkts-apis-audio-f.md#audiocreateaudiocapturer8)会创建失败。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

**系统接口：** 此接口为系统接口。
