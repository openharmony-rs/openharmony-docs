# PreferStrategy

```TypeScript
enum PreferStrategy
```

Preference strategy.

Example: With the global log level set to INFO, 5 logs of different levels are printed. setLogLevel is called twice during the printing process:

Since the global log starts at INFO, the first log can be printed normally.

After setting the process minimum log level to WARN with strategy PREFER_OPEN_LOG, the effective minimum log level is the global log level INFO, so both the second and third logs can be printed normally.

After setting the process minimum log level to DEBUG with strategy PREFER_CLOSE_LOG (equivalent to hilog.setMinLogLevel(hilog.LogLevel.DEBUG)), but the global log level is INFO at this time, so the fourth log does not meet the global log level and fails to print. The fifth log can be printed.

**Since:** 21

<!--Device-hilog-enum PreferStrategy--><!--Device-hilog-enum PreferStrategy-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## PREFER_CLOSE_LOG

```TypeScript
PREFER_CLOSE_LOG = 1
```

The effective minimum log level is the larger of the newly set level and the system-controlled minimum level. Suitable for scenarios that require strict restriction of log output.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-PreferStrategy-PREFER_CLOSE_LOG = 1--><!--Device-PreferStrategy-PREFER_CLOSE_LOG = 1-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## PREFER_OPEN_LOG

```TypeScript
PREFER_OPEN_LOG = 2
```

The effective minimum log level is the smaller of the newly set level and the system-controlled minimum level. Suitable for scenarios that require as much log output as possible.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-PreferStrategy-PREFER_OPEN_LOG = 2--><!--Device-PreferStrategy-PREFER_OPEN_LOG = 2-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## UNSET_LOGLEVEL

```TypeScript
UNSET_LOGLEVEL = 0
```

Clears the setting. The effective minimum log level is the minimum level controlled by the system.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-PreferStrategy-UNSET_LOGLEVEL = 0--><!--Device-PreferStrategy-UNSET_LOGLEVEL = 0-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog
