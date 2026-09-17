# AudioLoopbackStatus

Enumerates the audio loopback statuses.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## UNAVAILABLE_DEVICE

```TypeScript
UNAVAILABLE_DEVICE = -2
```

Loopback is unavailable due to issues with the input or output device (for example, changes in the audio output device).

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## UNAVAILABLE_SCENE

```TypeScript
UNAVAILABLE_SCENE = -1
```

Loopback is unavailable due to restrictions in the audio scene (for example, audio focus or low-latency management).

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## AVAILABLE_IDLE

```TypeScript
AVAILABLE_IDLE = 0
```

Loopback is available but currently idle.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## AVAILABLE_RUNNING

```TypeScript
AVAILABLE_RUNNING = 1
```

Loopback is actively running.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Capturer
