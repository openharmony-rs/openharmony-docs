# OutputType

Enumerates output type of hilog.

@enum { int }

**Since:** 26.0.0

**System capability:** SystemCapability.HiviewDFX.HiLog

## DEFAULT

```TypeScript
DEFAULT = 0
```

DEFAULT Default output type, equivalent to CONSOLE_ONLY.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiLog

## CONSOLE_ONLY

```TypeScript
CONSOLE_ONLY = 0
```

CONSOLE_ONLY Hilog is output to the console only, equivalent to DEFAULT.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiLog

## PRIVATE_SANDBOX_ONLY

```TypeScript
PRIVATE_SANDBOX_ONLY = 1
```

PRIVATE_SANDBOX_ONLY Hilog is output to files in its own private sandbox.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiLog

## SHARE_SANDBOX_ONLY

```TypeScript
SHARE_SANDBOX_ONLY = 2
```

SHARE_SANDBOX_ONLY Hilog is output to files in its own sandbox, accessible to itself and the hiview service.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiLog

## PRIVATE_SANDBOX_WITH_CONSOLE

```TypeScript
PRIVATE_SANDBOX_WITH_CONSOLE = 3
```

PRIVATE_SANDBOX_WITH_CONSOLE Enable both CONSOLE_ONLY and PRIVATE_SANDBOX_ONLY at the same time.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiLog

## SHARE_SANDBOX_WITH_CONSOLE

```TypeScript
SHARE_SANDBOX_WITH_CONSOLE = 4
```

SHARE_SANDBOX_WITH_CONSOLE Enable both CONSOLE_ONLY and SHARE_SANGBOX_ONLY at the same time.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiLog
