# InterruptForceType

Enumerates the types of force that causes audio interruption.

The force type is obtained when an [InterruptEvent](arkts-audio-audio-interruptevent-i.md) is received.

This type specifies whether audio interruption is forcibly performed by the system. The operation information (such as audio pause or stop) can be obtained through [InterruptHint](arkts-audio-audio-interrupthint-e.md). For details about the audio interruption policy, see [Introduction to Audio Focus](../../../media/audio/audio-playback-concurrency.md).

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_FORCE

```TypeScript
INTERRUPT_FORCE = 0
```

The operation is forcibly performed by the system.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_SHARE

```TypeScript
INTERRUPT_SHARE = 1
```

The operation will not be performed by the system. [InterruptHint](arkts-audio-audio-interrupthint-e.md) is used to provide recommended operations for the application, and the application can determine the next processing mode.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Renderer
