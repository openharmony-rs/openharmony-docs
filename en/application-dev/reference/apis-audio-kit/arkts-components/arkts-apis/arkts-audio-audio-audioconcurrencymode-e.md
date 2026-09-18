# AudioConcurrencyMode

Enumerates the audio concurrency modes.

@enum { int } [since 12 - 24]

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Core

## CONCURRENCY_DEFAULT

```TypeScript
CONCURRENCY_DEFAULT = 0
```

Uses the system strategy by default.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Audio.Core

## CONCURRENCY_MIX_WITH_OTHERS

```TypeScript
CONCURRENCY_MIX_WITH_OTHERS = 1
```

Concurrent with other audio streams, that is, audio mixing.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Audio.Core

## CONCURRENCY_DUCK_OTHERS

```TypeScript
CONCURRENCY_DUCK_OTHERS = 2
```

Ducks other audio streams.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Audio.Core

## CONCURRENCY_PAUSE_OTHERS

```TypeScript
CONCURRENCY_PAUSE_OTHERS = 3
```

Pauses other audio streams.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Audio.Core
