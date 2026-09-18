# HiTraceOutputLevel

Enumerates trace output levels.

The trace output level lower than the threshold does not take effect. The log version threshold is **INFO**, and the nolog version threshold is **COMMERCIAL**.

**Since:** 19

**System capability:** SystemCapability.HiviewDFX.HiTrace

## DEBUG

```TypeScript
DEBUG = 0
```

Level used only for debugging, which has the lowest priority.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.HiviewDFX.HiTrace

## INFO

```TypeScript
INFO = 1
```

Level for the log version.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.HiviewDFX.HiTrace

## CRITICAL

```TypeScript
CRITICAL = 2
```

Level for the log version, which has a higher priority than **INFO**.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.HiviewDFX.HiTrace

## COMMERCIAL

```TypeScript
COMMERCIAL = 3
```

Level for the nolog version, which has the highest priority.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.HiviewDFX.HiTrace

## MAX

```TypeScript
MAX = COMMERCIAL
```

Maximum trace output level: **COMMERCIAL**.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.HiviewDFX.HiTrace
