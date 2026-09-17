# AudioSessionStateChangeHint

Enumerates the hints for audio session state changes.

The hint is obtained when an [AudioSessionStateChangedEvent](arkts-audio-audio-audiosessionstatechangedevent-i.md) is received.

The hint specifies the action (such as audio pause or volume adjustment) to take on the audio session based on the focus strategy.

For details, see [Audio Session Management](../../../media/audio/audio-session-management.md).

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core

## AUDIO_SESSION_STATE_CHANGE_HINT_RESUME

```TypeScript
AUDIO_SESSION_STATE_CHANGE_HINT_RESUME = 0
```

A hint is displayed, indicating that the audio session is resuming. The application can proactively trigger operations such as rendering.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core

## AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE

```TypeScript
AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE = 1
```

A hint is displayed, indicating that the audio session is paused and the audio focus is lost temporarily. When focus is regained, the AUDIO_SESSION_STATE_CHANGE_HINT_RESUME event is received.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core

## AUDIO_SESSION_STATE_CHANGE_HINT_STOP

```TypeScript
AUDIO_SESSION_STATE_CHANGE_HINT_STOP = 2
```

A hint is displayed, indicating that the audio session is stopped and the audio focus is lost permanently.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core

## AUDIO_SESSION_STATE_CHANGE_HINT_TIME_OUT_STOP

```TypeScript
AUDIO_SESSION_STATE_CHANGE_HINT_TIME_OUT_STOP = 3
```

A hint is displayed, indicating that the audio session is stopped by the system due to no activity, and the audio focus is lost.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core

## AUDIO_SESSION_STATE_CHANGE_HINT_DUCK

```TypeScript
AUDIO_SESSION_STATE_CHANGE_HINT_DUCK = 4
```

A hint is displayed, indicating that audio ducking starts and the audio is played at a lower volume.

If [enableMuteSuggestionWhenMixWithOthers](arkts-audio-audio-audiosessionmanager-i.md#enablemutesuggestionwhenmixwithothers) is enabled, you can choose to mute the audio.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core

## AUDIO_SESSION_STATE_CHANGE_HINT_UNDUCK

```TypeScript
AUDIO_SESSION_STATE_CHANGE_HINT_UNDUCK = 5
```

A hint is displayed, indicating that audio ducking ends and the audio is played at the normal volume.

If [enableMuteSuggestionWhenMixWithOthers](arkts-audio-audio-audiosessionmanager-i.md#enablemutesuggestionwhenmixwithothers) is enabled, you can unmute the audio.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Core

## AUDIO_SESSION_STATE_CHANGE_HINT_MUTE_SUGGESTION

```TypeScript
AUDIO_SESSION_STATE_CHANGE_HINT_MUTE_SUGGESTION = 6
```

Suggests to mute the playback because there is another application begin to play nonmixable audio, application can decide whether to mute. If interrupt strategy is duck, [AUDIO_SESSION_STATE_CHANGE_HINT_DUCK](#audio_session_state_change_hint_duck) will replace mute suggestion event, but application can still decide to mute when receive hint duck.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

## AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE_SUGGESTION

```TypeScript
AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE_SUGGESTION = 7
```

Suggest to unmute the playback because another application's nonmixable audio ends, application can decide whether to mute. If interrupt strategy is unduck, [AUDIO_SESSION_STATE_CHANGE_HINT_UNDUCK](#audio_session_state_change_hint_unduck) will replace unmute suggestion event, but application can still decide to unmute when receive hint unduck.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

## AUDIO_SESSION_STATE_CHANGE_HINT_MUTE

```TypeScript
AUDIO_SESSION_STATE_CHANGE_HINT_MUTE = 8
```

The hint can be received only after the parameter [MUTE_WHEN_INTERRUPTED](arkts-audio-audio-audiosessionbehaviorflags-e.md#mute_when_interrupted) has been set by the interface [setAudioSessionBehavior](arkts-audio-audio-audiosessionmanager-i.md#setaudiosessionbehavior) and [setAudioSessionScene](arkts-audio-audio-audiosessionmanager-i.md#setaudiosessionscene) has been called, and the audio session has been activated. After the hint is received, the audio stream is muted.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

## AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE

```TypeScript
AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE = 9
```

The hint can be received only after the parameter [MUTE_WHEN_INTERRUPTED](arkts-audio-audio-audiosessionbehaviorflags-e.md#mute_when_interrupted) has been set by the interface [setAudioSessionBehavior](arkts-audio-audio-audiosessionmanager-i.md#setaudiosessionbehavior) and [setAudioSessionScene](arkts-audio-audio-audiosessionmanager-i.md#setaudiosessionscene) has been called, and the audio session has been activated. When the hint is received, the audio stream is unmuted.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core
