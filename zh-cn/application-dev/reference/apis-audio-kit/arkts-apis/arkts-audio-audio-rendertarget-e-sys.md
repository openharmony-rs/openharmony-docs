# RenderTarget（系统接口）

Audio render target.

**起始版本：** 22

<!--Device-audio-enum RenderTarget--><!--Device-audio-enum RenderTarget-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## PLAYBACK

```TypeScript
PLAYBACK = 0
```

Playback. Under this target, the audio renderer will be played out. This is the default target of audio renderer.

**起始版本：** 22

<!--Device-RenderTarget-PLAYBACK = 0--><!--Device-RenderTarget-PLAYBACK = 0-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## INJECT_TO_VOICE_COMMUNICATION_CAPTURE

```TypeScript
INJECT_TO_VOICE_COMMUNICATION_CAPTURE = 1
```

Inject to voice communication capture. Under this target, the audio renderer will be injected to audio capture with source type of {@link SourceType#SOURCE_TYPE_VOICE_COMMUNICATION} when the audio scene is {@link AudioScene#AUDIO_SCENE_VOICE_CHAT}.

**起始版本：** 22

<!--Device-RenderTarget-INJECT_TO_VOICE_COMMUNICATION_CAPTURE = 1--><!--Device-RenderTarget-INJECT_TO_VOICE_COMMUNICATION_CAPTURE = 1-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

