# AudioSessionBehaviorFlags

Enumerates audio session behavior flags.

**Since:** 24

**System capability:** SystemCapability.Multimedia.Audio.Core

## DEFAULT_BEHAVIOR

```TypeScript
DEFAULT_BEHAVIOR = 0x00000000
```

Default behavior, used to clear behavior settings.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

## MUTE_WHEN_INTERRUPTED

```TypeScript
MUTE_WHEN_INTERRUPTED = 0x00000002
```

When the system needs to stop or pause the audio stream, it performs a forced mute instead. In the audio session scenario, the application will receive a notification [AUDIO_SESSION_STATE_CHANGE_HINT_MUTE](arkts-audio-audio-audiosessionstatechangehint-e.md#audio_session_state_change_hint_mute) when muted and a notification [AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE](arkts-audio-audio-audiosessionstatechangehint-e.md#audio_session_state_change_hint_unmute) when resumed. In the AudioRenderer and AudioCapturer scenarios, the application will receive a notification [INTERRUPT_HINT_MUTE](arkts-audio-audio-interrupthint-e.md#interrupt_hint_mute) when muted and a notification [INTERRUPT_HINT_UNMUTE](arkts-audio-audio-interrupthint-e.md#interrupt_hint_unmute) when resumed. This flag cannot coexist with [PAUSE_WHEN_INTERRUPTED](#pause_when_interrupted); if both flags are set, only [PAUSE_WHEN_INTERRUPTED](#pause_when_interrupted) will take effect.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

## PAUSE_WHEN_INTERRUPTED

```TypeScript
PAUSE_WHEN_INTERRUPTED = 0x00000004
```

When the system needs to stop the audio stream, it performs a pause instead. In the audio session scenario, the application will receive a notification [AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE](arkts-audio-audio-audiosessionstatechangehint-e.md#audio_session_state_change_hint_pause) when paused and a notification [AUDIO_SESSION_STATE_CHANGE_HINT_RESUME](arkts-audio-audio-audiosessionstatechangehint-e.md#audio_session_state_change_hint_resume) when resumed. In the AudioRenderer and AudioCapturer scenarios, the application will receive a notification [INTERRUPT_HINT_PAUSE](arkts-audio-audio-interrupthint-e.md#interrupt_hint_pause) when paused and a notification [INTERRUPT_HINT_RESUME](arkts-audio-audio-interrupthint-e.md#interrupt_hint_resume) when resumed. This flag cannot coexist with [MUTE_WHEN_INTERRUPTED](#mute_when_interrupted); if both flags are set, only this flag will take effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core
