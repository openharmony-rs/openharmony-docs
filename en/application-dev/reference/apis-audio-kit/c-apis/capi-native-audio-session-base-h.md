# native_audio_session_base.h

## Overview

Declares the audio session base data structure.

**Library**: libohaudio.so

**Since**: 24

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Struct

| Name | Description |
| -- | -- |
| [OH_AudioSession_Strategy](capi-ohaudio-oh-audiosession-strategy.md) | Declares the audio session strategy. |

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
| MUTE_WHEN_INTERRUPTED = 0x00000002 | When the system needs to stop or pause the audio stream, it performs a forced mute instead. In the audio session scenario, the application will receive a notification [AUDIO_SESSION_STATE_CHANGE_HINT_MUTE](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint) when muted and a notification [AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint) when resumed. In the OH_AudioRenderer and OH_AudioCapturer scenarios, the application will receive a notification [AUDIOSTREAM_INTERRUPT_HINT_MUTE](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint) when muted and a notification [AUDIOSTREAM_INTERRUPT_HINT_UNMUTE](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint) when resumed. This flag cannot coexist with [PAUSE_WHEN_INTERRUPTED](capi-native-audio-session-base-h.md#oh_audiosession_behaviorflags); if both flags are set, only [PAUSE_WHEN_INTERRUPTED](capi-native-audio-session-base-h.md#oh_audiosession_behaviorflags) will take effect.<br>**Since**: 24 |
| PAUSE_WHEN_INTERRUPTED = 0x00000004 | When the system needs to stop the audio stream, it performs a pause instead. In the audio session scenario, the application will receive a notification [AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint) when paused and a notification [AUDIO_SESSION_STATE_CHANGE_HINT_RESUME](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint) when resumed. In the OH_AudioRenderer and OH_AudioCapturer scenarios, the application will receive a notification [AUDIOSTREAM_INTERRUPT_HINT_PAUSE](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint) when paused and a notification [AUDIOSTREAM_INTERRUPT_HINT_RESUME](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint) when resumed. This flag cannot coexist with [MUTE_WHEN_INTERRUPTED](capi-native-audio-session-base-h.md#oh_audiosession_behaviorflags); if both flags are set, only this flag will take effect.<br>**Since**: 26.0.0 |

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


