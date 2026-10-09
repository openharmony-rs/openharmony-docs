# native_audio_session_base.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## Overview

The file declares the basic data struct of an audio session.

**File to include**: <ohaudio/native_audio_session_base.h>

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 24

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AudioSession_Strategy](capi-ohaudio-oh-audiosession-strategy.md) | OH_AudioSession_Strategy | Describes the audio session strategy.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AudioSession_BehaviorFlags](#oh_audiosession_behaviorflags) | OH_AudioSession_BehaviorFlags | Enumerates the audio session behavior flags.|
| [OH_AudioSession_ConcurrencyMode](#oh_audiosession_concurrencymode) | OH_AudioSession_ConcurrencyMode | Enumerates the audio concurrency modes.|

## Enum Description

### OH_AudioSession_BehaviorFlags

```c
enum OH_AudioSession_BehaviorFlags
```

**Description**

Enumerates the audio session behavior flags.

**Since**: 24

| Enum Item| Description|
| -- | -- |
| DEFAULT_BEHAVIOR = 0x00000000 | Default behavior, which is used to clear the session behavior flag.<br>**Since**: 24|
| VOIP_PRIVACY_TYPE_PUBLIC = 0x00000001 | Non-private VoIP, which can be recorded. Concurrent recording of VoIP streams and other application streams are supported.<br>**Since**: 26.0.0|
| MUTE_WHEN_INTERRUPTED = 0x00000002 | Mute the audio stream when it is interrupted. You need to call [OH_AudioSessionManager_SetBehavior](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setbehavior) to set the behavior and call [OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene) to make it take effect. An application will receive an [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_INTERRUPT_HINT_MUTE notification when playback is muted, and an [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_INTERRUPT_HINT_UNMUTE notification when the playback is unmuted.<br>**Since**: 24|

### OH_AudioSession_ConcurrencyMode

```c
enum OH_AudioSession_ConcurrencyMode
```

**Description**

Enumerates the audio concurrency modes.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| CONCURRENCY_DEFAULT = 0 | The system strategy is used by default.|
| CONCURRENCY_MIX_WITH_OTHERS = 1 | The current application mixes audio with other applications during playback.|
| CONCURRENCY_DUCK_OTHERS = 2 | The current application ducks the volume of other playing applications during playback.|
| CONCURRENCY_PAUSE_OTHERS = 3 | The current application pauses other playing applications during playback.|
