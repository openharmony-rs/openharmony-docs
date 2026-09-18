# LogLevel

Enumerates the log levels.

**Since:** 7

**System capability:** SystemCapability.HiviewDFX.HiLog

## DEBUG

```TypeScript
DEBUG = 3
```

Log level used to record more detailed process information than INFO logs to help developers analyze service processes and locate faults.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiLog

## INFO

```TypeScript
INFO = 4
```

Log level used to record key service process nodes and exceptions that occur during service running,

for example, no network signal or login failure.

These logs should be recorded by the dominant module in the service to avoid repeated logging conducted by multiple invoked modules or low-level functions.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiLog

## WARN

```TypeScript
WARN = 5
```

Log level used to record severe, unexpected faults that have little impact on users and can be rectified by the programs themselves or through simple operations.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiLog

## ERROR

```TypeScript
ERROR = 6
```

Log level used to record program or functional errors that affect the normal running or use of the functionality and can be fixed at a high cost, for example, by resetting data.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiLog

## FATAL

```TypeScript
FATAL = 7
```

Log level used to record program or functionality crashes that cannot be rectified.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiLog
