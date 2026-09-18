# InterruptHint

Enumerates the hints provided along with audio interruption.

The hint is obtained when an [InterruptEvent](arkts-audio-audio-interruptevent-i.md) is received.

The hint specifies the operation (such as audio pause or volume adjustment) to be performed on audio streams based on the focus strategy.

You can determine whether the operation is forcibly performed by the system based on [InterruptForceType](arkts-audio-audio-interruptforcetype-e.md) in **InterruptEvent**. For details, see [Introduction to Audio Focus](../../../media/audio/audio-playback-concurrency.md).

**Since:** 7

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_NONE

```TypeScript
INTERRUPT_HINT_NONE = 0
```

None.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_RESUME

```TypeScript
INTERRUPT_HINT_RESUME = 1
```

A hint is displayed, indicating that the audio stream is restored. The application can proactively trigger operations related to rendering or recording.

This operation cannot be forcibly performed by the system, and the corresponding [InterruptForceType](arkts-audio-audio-interruptforcetype-e.md) must be **INTERRUPT_SHARE**.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_PAUSE

```TypeScript
INTERRUPT_HINT_PAUSE = 2
```

A hint is displayed, indicating that the audio stream is paused and the audio focus is lost temporarily.

When the audio focus is available, the **INTERRUPT_HINT_RESUME** event is received.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_STOP

```TypeScript
INTERRUPT_HINT_STOP = 3
```

A hint is displayed, indicating that the audio stream stops and the audio focus is lost.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_DUCK

```TypeScript
INTERRUPT_HINT_DUCK = 4
```

A hint is displayed, indicating that audio ducking starts and the audio is played at a lower volume.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_UNDUCK

```TypeScript
INTERRUPT_HINT_UNDUCK = 5
```

A hint is displayed, indicating that audio ducking ends and the audio is played at the normal volume.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_MUTE

```TypeScript
INTERRUPT_HINT_MUTE = 6
```

A hint is displayed, indicating that the audio is muted.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_HINT_UNMUTE

```TypeScript
INTERRUPT_HINT_UNMUTE = 7
```

A hint is displayed, indicating that the audio is unmuted.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Renderer
