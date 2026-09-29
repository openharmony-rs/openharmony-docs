# PreferStrategy

```TypeScript
enum PreferStrategy
```

Enumerates the preference strategies.

**Since:** 21

<!--Device-hilog-enum PreferStrategy--><!--Device-hilog-enum PreferStrategy-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## UNSET_LOGLEVEL

```TypeScript
UNSET_LOGLEVEL = 0
```

The setting is cleared. The system-controlled minimum log level takes effect.

**Since:** 21

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 21.

<!--Device-PreferStrategy-UNSET_LOGLEVEL = 0--><!--Device-PreferStrategy-UNSET_LOGLEVEL = 0-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## PREFER_CLOSE_LOG

```TypeScript
PREFER_CLOSE_LOG = 1
```

The larger value of the new log level and the system-controlled minimum log level takes effect.

**Since:** 21

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 21.

<!--Device-PreferStrategy-PREFER_CLOSE_LOG = 1--><!--Device-PreferStrategy-PREFER_CLOSE_LOG = 1-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## PREFER_OPEN_LOG

```TypeScript
PREFER_OPEN_LOG = 2
```

The smaller value of the new log level and the system-controlled minimum log level takes effect.

**Since:** 21

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 21.

<!--Device-PreferStrategy-PREFER_OPEN_LOG = 2--><!--Device-PreferStrategy-PREFER_OPEN_LOG = 2-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog
