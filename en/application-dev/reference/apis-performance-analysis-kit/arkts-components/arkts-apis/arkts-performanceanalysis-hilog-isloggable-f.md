# isLoggable

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## isLoggable

```TypeScript
function isLoggable(domain: number, tag: string, level: LogLevel): boolean
```

Checks whether logs are printable based on the specified service domain, log tag, and log level.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiLog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domain | number | Yes | Service domain of logs. The value ranges from **0x0** to **0xFFFF**. If the value exceeds the range, logs cannot be printed.<br>You can define the value as required. |
| tag | string | Yes | Log tag in the string format. You are advised to use this parameter to identify a particular service behavior or the class holding the ongoing method. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur. |
| level | [LogLevel](arkts-performanceanalysis-hilog-loglevel-e.md) | Yes | Log level. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** logs are printable based on the specified service domain, log tag, and log level; returns **false** otherwise. |

**Examples**

```TypeScript
hilog.isLoggable(0x0001, "testTag", hilog.LogLevel.INFO);
```
