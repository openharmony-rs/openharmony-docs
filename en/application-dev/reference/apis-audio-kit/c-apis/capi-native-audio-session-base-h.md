# native_audio_session_base.h

## Overview

Declares the audio session base data structure.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioSession_Strategy](capi-ohaudio-oh-audiosession-strategy.md) | OH_AudioSession_Strategy | Declares the audio session strategy. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioSession_BehaviorFlags](#oh_audiosession_behaviorflags) | OH_AudioSession_BehaviorFlags | Enumerates the audio session behavior flags. |
| [OH_AudioSession_ConcurrencyMode](#oh_audiosession_concurrencymode) | OH_AudioSession_ConcurrencyMode | Declares the audio concurrency modes. |

## Enum type description

### OH_AudioSession_BehaviorFlags

```c
enum OH_AudioSession_BehaviorFlags
```

**Description**

Enumerates the audio session behavior flags.

**Since**: 24

| Enum item | Description |
| -- | -- |
| DEFAULT_BEHAVIOR  = 0x00000000 | Default behavior, used to clear behavior settings.<br>**Since**: 24 |
| MUTE_WHEN_INTERRUPTED = 0x00000002 | When the system needs to stop or pause the audio stream, it performs a forced mute instead. In the audio session scenario, the application will receive a notification {@link AUDIO_SESSION_STATE_CHANGE_HINT_MUTE} when muted<br>and a notification {@link AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE} when resumed.<br>In the OH_AudioRenderer and OH_AudioCapturer scenarios, the application will receive a notification<br>{@link AUDIOSTREAM_INTERRUPT_HINT_MUTE} when muted<br>and a notification {@link AUDIOSTREAM_INTERRUPT_HINT_UNMUTE} when resumed. This flag cannot coexist with [PAUSE_WHEN_INTERRUPTED](capi-native-audio-session-base-h.md#oh_audiosession_behaviorflags); if both flags are set,<br>only [PAUSE_WHEN_INTERRUPTED](capi-native-audio-session-base-h.md#oh_audiosession_behaviorflags) will take effect.<br>**Since**: 24 |
| PAUSE_WHEN_INTERRUPTED = 0x00000004 | When the system needs to stop the audio stream, it performs a pause instead. In the audio session scenario, the application will receive a notification {@link AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE} when paused<br>and a notification {@link AUDIO_SESSION_STATE_CHANGE_HINT_RESUME} when resumed.<br>In the OH_AudioRenderer and OH_AudioCapturer scenarios, the application will receive a notification<br>{@link AUDIOSTREAM_INTERRUPT_HINT_PAUSE} when paused<br>and a notification {@link AUDIOSTREAM_INTERRUPT_HINT_RESUME} when resumed. This flag cannot coexist with [MUTE_WHEN_INTERRUPTED](capi-native-audio-session-base-h.md#oh_audiosession_behaviorflags); if both flags are set, only this flag will take effect.<br>**Since**: 26.0.0 |

### OH_AudioSession_ConcurrencyMode

```c
enum OH_AudioSession_ConcurrencyMode
```

**Description**

Declares the audio concurrency modes.

**Since**: 12

| Enum item | Description |
| -- | -- |
| CONCURRENCY_DEFAULT = 0 | Default mode |
| CONCURRENCY_MIX_WITH_OTHERS = 1 | Mix with others mode |
| CONCURRENCY_DUCK_OTHERS = 2 | Duck others mode |
| CONCURRENCY_PAUSE_OTHERS = 3 | Pause others mode |


