# AudioPrivacyType

表示对应播放音频流是否支持被其他应用录制的枚举。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## PRIVACY_TYPE_PUBLIC

```TypeScript
PRIVACY_TYPE_PUBLIC = 0
```

表示音频流可以被其他应用录制或屏幕投射，不包含隐私类型的流。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## PRIVACY_TYPE_PRIVATE

```TypeScript
PRIVACY_TYPE_PRIVATE = 1
```

表示音频流不可以被其他应用录制或屏幕投射。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## PRIVACY_TYPE_SHARED

```TypeScript
PRIVACY_TYPE_SHARED = 2
```

表示音频流可以被其他应用录制或屏幕投射，包含隐私类型的流。

例如，在PRIVACY_TYPE_PUBLIC策略下，[STREAM_USAGE_VOICE_COMMUNICATION](arkts-audio-streamusage-e.md)类型音频流不会被其他应用录制或屏幕投射。

然而，在PRIVACY_TYPE_SHARED策略下，这些音频流将会允许被其他应用录制或屏幕投射。

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

