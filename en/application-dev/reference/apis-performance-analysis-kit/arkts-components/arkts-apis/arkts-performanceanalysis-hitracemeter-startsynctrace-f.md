# startSyncTrace

## Modules to Import

```TypeScript
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## startSyncTrace

```TypeScript
function startSyncTrace(level: HiTraceOutputLevel, name: string, customArgs?: string): void
```

Starts a synchronous trace with the trace output level specified. For details, see [finishSyncTrace()](arkts-performanceanalysis-hitracemeter-finishsynctrace-f.md).

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| level | [HiTraceOutputLevel](arkts-performanceanalysis-hitracemeter-hitraceoutputlevel-e.md) | Yes | Trace output level. |
| name | string | Yes | Name of the trace to start. The maximum length of a trace record is 512 bytes. The excess part will be truncated. It is recommended that the total length of **name** and **customArgs** be less than or equal to 420 bytes. |
| customArgs | string | No | Key-value pair. The format is key=value. Multiple key-value pairs are separated by commas (,). The default value is an empty string. The maximum length of a trace record is 512 bytes. The excess part will be truncated. It is recommended that the total length of **name** and **customArgs** be less than or equal to 420 bytes. |

**Examples**

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
// If the customArgs parameter is not required, do not pass in this parameter or pass in an empty string.
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc");
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc", "");
// Use commas (,) to separate multiple key-value pairs.
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc", "key=value");
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc", "key1=value1,key2=value2");
```
