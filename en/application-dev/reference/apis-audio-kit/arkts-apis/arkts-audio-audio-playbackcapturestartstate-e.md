# PlaybackCaptureStartState

Defines the playback capture start state, which is returned asynchronously after calling [requestPlaybackCaptureStart](arkts-audio-audio-audiocapturer-i.md#requestplaybackcapturestart) function.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

## STATE_SUCCESS

```TypeScript
STATE_SUCCESS = 0
```

Start playback capture success state.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

## STATE_FAILED

```TypeScript
STATE_FAILED = 1
```

Start playback capture failed state, because the request for interrupt is denied or meet system internal error.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

## STATE_NOT_AUTHORIZED

```TypeScript
STATE_NOT_AUTHORIZED = 2
```

Start playback capture but user not authorized state.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture
