# isLoggable

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## isLoggable

```TypeScript
function isLoggable(domain: number, tag: string, level: LogLevel): boolean
```

Called before printing a log to check whether a log with the specified domain identifier, tag, and level can be printed.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-hilog-function isLoggable(domain: int, tag: string, level: LogLevel): boolean--><!--Device-hilog-function isLoggable(domain: int, tag: string, level: LogLevel): boolean-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domain | number | Yes | Domain identifier for the log, ranging from 0x0 to 0xFFFF. Logs outside this range cannot be printed.<br>It is recommended that developers define and divide domains as needed within the application. |
| tag | string | Yes | Specifies the log tag, which can be any string. It is recommended to identify the calling class or business behavior. The recommended tag length should not exceed 31 bytes. Chinese characters are not recommended as they may cause garbled text or alignment issues. |
| level | [LogLevel](arkts-performanceanalysis-hilog-loglevel-e.md) | Yes | Log level. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the log with the specified domain identifier, tag, and level can be printed; otherwise false. |

**Examples**

```TypeScript
hilog.isLoggable(0x0001, "testTag", hilog.LogLevel.INFO);
```
