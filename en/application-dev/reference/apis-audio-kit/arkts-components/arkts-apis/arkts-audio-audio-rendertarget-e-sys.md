# RenderTarget (System API)

Audio render target.

**Since:** 22

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

## PLAYBACK

```TypeScript
PLAYBACK = 0
```

Playback. Under this target, the audio renderer will be played out. This is the default target of audio renderer.

**Since:** 22

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

## INJECT_TO_VOICE_COMMUNICATION_CAPTURE

```TypeScript
INJECT_TO_VOICE_COMMUNICATION_CAPTURE = 1
```

Inject to voice communication capture. Under this target, the audio renderer will be injected to audio capture with source type of [SOURCE_TYPE_VOICE_COMMUNICATION](arkts-audio-audio-sourcetype-e.md#source_type_voice_communication) when the audio scene is [AUDIO_SCENE_VOICE_CHAT](arkts-audio-audio-audioscene-e.md#audio_scene_voice_chat).

**Since:** 22

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.
