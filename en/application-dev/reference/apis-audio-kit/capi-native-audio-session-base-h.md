# native_audio_session_base.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @funny_sunix-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=3553df6e5d67007804f181f4e162c866c01a26ba translatedAt=2026-11-09T10:24:20.121Z pushedAt=2026-11-09T11:24:56.774Z nl=1 -->

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
| MUTE_WHEN_INTERRUPTED = 0x00000002 | When the system needs to stop or pause the audio stream, forced mute is performed instead.<br>When calling [OH_AudioSessionManager_SetBehavior](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setbehavior) to configure this behavior, you must also call [OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene); otherwise, the configuration will not take effect.<br>In the audio session scenario, when the audio stream is muted or restored, the application receives the [OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint).AUDIO_SESSION_STATE_CHANGE_HINT_MUTE and [OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint).AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE notifications, respectively.<br>In the OH_AudioRenderer and OH_AudioCapturer scenarios, when the audio stream is muted or restored, the application receives the [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint).AUDIOSTREAM_INTERRUPT_HINT_MUTE and [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint).AUDIOSTREAM_INTERRUPT_HINT_UNMUTE notifications, respectively.<br/>**Note:** This flag cannot coexist with PAUSE_WHEN_INTERRUPTED. If both are set, only PAUSE_WHEN_INTERRUPTED takes effect.<br>**Since:** 24 |
| PAUSE_WHEN_INTERRUPTED = 0x00000004 | When the system needs to stop the audio stream, pause is performed instead.<br>When calling [OH_AudioSessionManager_SetBehavior](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setbehavior) to configure this behavior, you must also call [OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene); otherwise, the configuration will not take effect.<br>In the audio session scenario, when the audio stream is paused or resumed, the application receives the [OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint).AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE and [OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint).AUDIO_SESSION_STATE_CHANGE_HINT_RESUME notifications, respectively.<br>In the OH_AudioRenderer and OH_AudioCapturer scenarios, when the audio stream is paused or resumed, the application receives the [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint).AUDIOSTREAM_INTERRUPT_HINT_PAUSE and [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint).AUDIOSTREAM_INTERRUPT_HINT_RESUME notifications, respectively.<br/>**Note:** This flag cannot coexist with MUTE_WHEN_INTERRUPTED. If both are set, only this flag takes effect.<br>**Since:** 26.0.0 |

### OH_AudioSession_ConcurrencyMode

```c
enum OH_AudioSession_ConcurrencyMode
```

**Description**

Enumerates the audio concurrency modes.

Since API version 24, this enum has been moved from native_audio_session_manager.h to this header file.

Before API version 24, include native_audio_session_manager.h to use this enum. Since API version 24, you can include either native_audio_session_manager.h or native_audio_session_base.h to use this enum.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| CONCURRENCY_DEFAULT = 0 | The system strategy is used by default.|
| CONCURRENCY_MIX_WITH_OTHERS = 1 | The current application mixes audio with other applications during playback.|
| CONCURRENCY_DUCK_OTHERS = 2 | The current application ducks the volume of other playing applications during playback.|
| CONCURRENCY_PAUSE_OTHERS = 3 | The current application pauses other playing applications during playback.|


