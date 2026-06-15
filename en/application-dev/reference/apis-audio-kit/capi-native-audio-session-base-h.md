# native_audio_session_base.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @funny_sunix-->
<!--Designer: @hao-liangfei-->
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
| MUTE_WHEN_INTERRUPTED = 0x00000002 | When the system needs to stop or pause an audio stream, forced muting is applied as an alternative.<br>When the [OH_AudioSessionManager_SetBehavior](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setbehavior) API is called to configure this behavior, the [OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene) API must also be called. Otherwise, the configuration will not take effect.<br>In audio session scenarios, when an audio stream is muted or unmuted, the application will receive the [OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint).AUDIO_SESSION_STATE_CHANGE_HINT_MUTE and [OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint).AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE notifications, respectively.<br>In OH_AudioRenderer and OH_AudioCapturer scenarios, when an audio stream is muted or unmuted, the application will receive the [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint).AUDIOSTREAM_INTERRUPT_HINT_MUTE and [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint).AUDIOSTREAM_INTERRUPT_HINT_UNMUTE notifications, respectively.<br>**Since**: 24|

### OH_AudioSession_ConcurrencyMode

```c
enum OH_AudioSession_ConcurrencyMode
```

**Description**

Enumerates the audio concurrency modes.

This enum is moved from **native_audio_session_manager.h** to this header file since API version 24.

Before API version 24, use this enum only when **native_audio_session_manager.h** is referenced. Since API version 24, this enum can be used as long as **native_audio_session_manager.h** or **native_audio_session_base.h** is referenced.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| CONCURRENCY_DEFAULT = 0 | The system strategy is used by default.|
| CONCURRENCY_MIX_WITH_OTHERS = 1 | The current application mixes audio with other applications during playback.|
| CONCURRENCY_DUCK_OTHERS = 2 | The current application ducks the volume of other playing applications during playback.|
| CONCURRENCY_PAUSE_OTHERS = 3 | The current application pauses other playing applications during playback.|
