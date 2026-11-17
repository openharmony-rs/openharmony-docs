# OutputType

```TypeScript
enum OutputType
```

Enum values for hilog output types. DEFAULT and CONSOLE_ONLY are suitable for console-only output scenarios, PRIVATE_SANDBOX_ONLY is suitable for privacy log storage, SHARE_SANDBOX_ONLY is suitable for scenarios requiring cloud log collection, PRIVATE_SANDBOX_WITH_CONSOLE and SHARE_SANDBOX_WITH_CONSOLE are suitable for scenarios requiring both console output and sandbox storage.

**Since:** 26.0.0

<!--Device-hilog-enum OutputType--><!--Device-hilog-enum OutputType-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## CONSOLE_ONLY

```TypeScript
CONSOLE_ONLY = 0
```

hilog outputs to console only, equivalent to DEFAULT.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OutputType-CONSOLE_ONLY = 0--><!--Device-OutputType-CONSOLE_ONLY = 0-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## DEFAULT

```TypeScript
DEFAULT = 0
```

Default output type. hilog outputs to console only, equivalent to CONSOLE_ONLY.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OutputType-DEFAULT = 0--><!--Device-OutputType-DEFAULT = 0-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## PRIVATE_SANDBOX_ONLY

```TypeScript
PRIVATE_SANDBOX_ONLY = 1
```

hilog logs are persisted to the application private sandbox. This path is only accessible by the application itself.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OutputType-PRIVATE_SANDBOX_ONLY = 1--><!--Device-OutputType-PRIVATE_SANDBOX_ONLY = 1-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## PRIVATE_SANDBOX_WITH_CONSOLE

```TypeScript
PRIVATE_SANDBOX_WITH_CONSOLE = 3
```

Simultaneously enables CONSOLE_ONLY and PRIVATE_SANDBOX_ONLY.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OutputType-PRIVATE_SANDBOX_WITH_CONSOLE = 3--><!--Device-OutputType-PRIVATE_SANDBOX_WITH_CONSOLE = 3-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## SHARE_SANDBOX_ONLY

```TypeScript
SHARE_SANDBOX_ONLY = 2
```

hilog logs are persisted to the application shared sandbox. This path is accessible by both the application and the system.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OutputType-SHARE_SANDBOX_ONLY = 2--><!--Device-OutputType-SHARE_SANDBOX_ONLY = 2-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## SHARE_SANDBOX_WITH_CONSOLE

```TypeScript
SHARE_SANDBOX_WITH_CONSOLE = 4
```

Simultaneously enables CONSOLE_ONLY and SHARE_SANDBOX_ONLY.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OutputType-SHARE_SANDBOX_WITH_CONSOLE = 4--><!--Device-OutputType-SHARE_SANDBOX_WITH_CONSOLE = 4-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog
