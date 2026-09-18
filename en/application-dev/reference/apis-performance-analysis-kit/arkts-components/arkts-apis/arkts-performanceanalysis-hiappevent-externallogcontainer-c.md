# ExternalLogContainer

An external log container including all external log files.

**Since:** 26.1.0

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## getAllLogFiles

```TypeScript
getAllLogFiles(): Set<string>
```

Get the set of all external log file paths

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Return value:**

| Type | Description |
| --- | --- |
| Set&lt;string&gt; | The set of all external log file paths |

## getAllLogs

```TypeScript
getAllLogs(): Set<ExternalLogWrapper>
```

Get the set of all ExternalLogWrappers

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Return value:**

| Type | Description |
| --- | --- |
| Set&lt;[ExternalLogWrapper](arkts-performanceanalysis-hiappevent-externallogwrapper-c.md)&gt; | The set of all ExternalLogWrappers |

## getFirstGeneratedLogFiles

```TypeScript
getFirstGeneratedLogFiles(num: number): Set<string>
```

Get the first generated external log file paths of a given number

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| num | number | Yes | given number of queried files |

**Return value:**

| Type | Description |
| --- | --- |
| Set&lt;string&gt; | The set of qualified external log file paths |

## getLogFilesGeneratedAfter

```TypeScript
getLogFilesGeneratedAfter(timePoint: number): Set<string>
```

Get the set of all external log file paths which are after a given time

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timePoint | number | Yes | given generated time point (ms) of file size |

**Return value:**

| Type | Description |
| --- | --- |
| Set&lt;string&gt; | The set of all external log file paths which are after a given time |

## getLogFilesGeneratedBefore

```TypeScript
getLogFilesGeneratedBefore(timePoint: number): Set<string>
```

Get the set of all external log file paths which are before a given time

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timePoint | number | Yes | given generated time point (ms) of file size |

**Return value:**

| Type | Description |
| --- | --- |
| Set&lt;string&gt; | The set of all external log file paths which are before a given time |

## getLogFilesLargerThan

```TypeScript
getLogFilesLargerThan(sizeKb: number): Set<string>
```

Get the set of all external log file paths whose size are larger than a given amount

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sizeKb | number | Yes | given amount of file size |

**Return value:**

| Type | Description |
| --- | --- |
| Set&lt;string&gt; | The set of all external log file paths whose size are larger than a given amount |

## getLogFilesOfSysEvent

```TypeScript
getLogFilesOfSysEvent(event: string): Set<string>
```

Get the set of all external log file paths of a given system event

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | string of given system event |

**Return value:**

| Type | Description |
| --- | --- |
| Set&lt;string&gt; | The set of all external log file paths of a given system event |

## getLogFilesSmallerThan

```TypeScript
getLogFilesSmallerThan(sizeKb: number): Set<string>
```

Get the set of all external log file paths whose size are smaller than a given amount

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sizeKb | number | Yes | given amount of file size |

**Return value:**

| Type | Description |
| --- | --- |
| Set&lt;string&gt; | The set of all external log file paths whose size are smaller than a given amount |

## getLogNumber

```TypeScript
getLogNumber(): number
```

Get the number of all external log files

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Return value:**

| Type | Description |
| --- | --- |
| number | The number of all external log files |
