# LogLevel

```TypeScript
enum LogLevel
```

Log level.

**Since:** 7

<!--Device-hilog-enum LogLevel--><!--Device-hilog-enum LogLevel-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## DEBUG

```TypeScript
DEBUG = 3
```

Detailed process records. Logs at this level can be used to analyze business processes and locate issues in detail.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LogLevel-DEBUG = 3--><!--Device-LogLevel-DEBUG = 3-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## ERROR

```TypeScript
ERROR = 6
```

The application has encountered an error that affects normal function operation or user experience. Recovery is possible but at a high cost, such as resetting data.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LogLevel-ERROR = 6--><!--Device-LogLevel-ERROR = 6-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## FATAL

```TypeScript
FATAL = 7
```

A major fatal exception indicating that the application is about to crash and the fault cannot be recovered.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LogLevel-FATAL = 7--><!--Device-LogLevel-FATAL = 7-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## INFO

```TypeScript
INFO = 4
```

Used to record key business process nodes, which can restore the main running process of the business;

Used to record information about expected abnormal situations, such as no network signal, login failure, etc.

These logs should be recorded by the dominant module in the business, avoiding duplicate recording in multiple called modules or low-level functions.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LogLevel-INFO = 4--><!--Device-LogLevel-INFO = 4-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## WARN

```TypeScript
WARN = 5
```

Used to record relatively severe unexpected situations that have little impact on users. The application can recover automatically or through simple operations.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LogLevel-WARN = 5--><!--Device-LogLevel-WARN = 5-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog
