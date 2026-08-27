# RenderTarget（系统接口）

枚举，音频渲染器的渲染目标。@enum { number }

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## PLAYBACK

```TypeScript
PLAYBACK = 0
```

播放模式（音频渲染器的默认模式）。在此模式下，音频将通过音频渲染器正常播放。

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## INJECT_TO_VOICE_COMMUNICATION_CAPTURE

```TypeScript
INJECT_TO_VOICE_COMMUNICATION_CAPTURE = 1
```

注入模式。在此模式下，当录音流的source type为[SOURCE_TYPE_VOICE_COMMUNICATION](arkts-apis-audio-e.md#sourcetype8)，audio scene为 [AUDIO_SCENE_VOICE_CHAT](arkts-apis-audio-e.md#audioscene)时，音频渲染器的输出将被注入到VoIP录音流上。

**起始版本：** 22

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。
