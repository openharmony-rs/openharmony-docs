# SourceType

表示录制音频流类型的枚举。

**起始版本：** 8

<!--Device-audio-enum SourceType--><!--Device-audio-enum SourceType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_INVALID

```TypeScript
SOURCE_TYPE_INVALID = -1
```

无效的音频源。

**起始版本：** 8

<!--Device-SourceType-SOURCE_TYPE_INVALID = -1--><!--Device-SourceType-SOURCE_TYPE_INVALID = -1-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_MIC

```TypeScript
SOURCE_TYPE_MIC = 0
```

Mic音频源。

**起始版本：** 8

<!--Device-SourceType-SOURCE_TYPE_MIC = 0--><!--Device-SourceType-SOURCE_TYPE_MIC = 0-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_VOICE_RECOGNITION

```TypeScript
SOURCE_TYPE_VOICE_RECOGNITION = 1
```

语音识别源。

**起始版本：** 9

<!--Device-SourceType-SOURCE_TYPE_VOICE_RECOGNITION = 1--><!--Device-SourceType-SOURCE_TYPE_VOICE_RECOGNITION = 1-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_PLAYBACK_CAPTURE

```TypeScript
SOURCE_TYPE_PLAYBACK_CAPTURE = 2
```

播放音频流（内录）录制音频源。

<br/

**起始版本：** 10

**废弃版本：** 12

**替代接口：** OH_AVScreenCapture

<!--Device-SourceType-SOURCE_TYPE_PLAYBACK_CAPTURE = 2--><!--Device-SourceType-SOURCE_TYPE_PLAYBACK_CAPTURE = 2-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## SOURCE_TYPE_VOICE_COMMUNICATION

```TypeScript
SOURCE_TYPE_VOICE_COMMUNICATION = 7
```

语音通话场景的音频源（单独启动录制不会开启3A算法，需同时使用[STREAM_USAGE_VOICE_COMMUNICATION](arkts-audio-audio-streamusage-e.md)或[STREAM_USAGE_VIDEO_COMMUNICATION](arkts-audio-audio-streamusage-e.md)类型的AudioRender起播才会触发开启3A算法）。

**起始版本：** 8

<!--Device-SourceType-SOURCE_TYPE_VOICE_COMMUNICATION = 7--><!--Device-SourceType-SOURCE_TYPE_VOICE_COMMUNICATION = 7-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_VOICE_MESSAGE

```TypeScript
SOURCE_TYPE_VOICE_MESSAGE = 10
```

短语音消息的音频源。

**起始版本：** 12

<!--Device-SourceType-SOURCE_TYPE_VOICE_MESSAGE = 10--><!--Device-SourceType-SOURCE_TYPE_VOICE_MESSAGE = 10-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_CAMCORDER

```TypeScript
SOURCE_TYPE_CAMCORDER = 13
```

录像的音频源。

**起始版本：** 13

<!--Device-SourceType-SOURCE_TYPE_CAMCORDER = 13--><!--Device-SourceType-SOURCE_TYPE_CAMCORDER = 13-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_UNPROCESSED

```TypeScript
SOURCE_TYPE_UNPROCESSED = 14
```

麦克风纯净录音的音频源（系统不做任何算法处理）。

**起始版本：** 14

<!--Device-SourceType-SOURCE_TYPE_UNPROCESSED = 14--><!--Device-SourceType-SOURCE_TYPE_UNPROCESSED = 14-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## SOURCE_TYPE_LIVE

```TypeScript
SOURCE_TYPE_LIVE = 17
```

直播场景的音频源，在支持的设备上会提供系统回声消除能力。

**起始版本：** 20

<!--Device-SourceType-SOURCE_TYPE_LIVE = 17--><!--Device-SourceType-SOURCE_TYPE_LIVE = 17-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

