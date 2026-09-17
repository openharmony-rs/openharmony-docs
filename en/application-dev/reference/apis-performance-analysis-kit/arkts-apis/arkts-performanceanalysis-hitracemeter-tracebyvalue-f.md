# traceByValue

## Modules to Import

```TypeScript
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## traceByValue

```TypeScript
function traceByValue(name: string, count: number): void
```

Traces the value changes of an integer variable.

Since API version 19, you are advised to use the [traceByValue](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md) API to specify the trace output level.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the integer variable to trace. The maximum length of a trace record is 512 bytes. The excess part will be truncated. It is recommended that the length of this parameter be less than or equal to 420 bytes. |
| count | number | Yes | Value of an integer variable. |

**Examples**

```TypeScript
let traceCount = 3;  // Define the initial value of the integer variable to be traced.
hiTraceMeter.traceByValue("myTestCount", traceCount);
traceCount = 4;
hiTraceMeter.traceByValue("myTestCount", traceCount);  // When myTestCount changes, the new value is recorded.
// Service flow...
```

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
let traceCount = 3;
hiTraceMeter.traceByValue(COMMERCIAL, "myTestCount", traceCount);
traceCount = 4;
hiTraceMeter.traceByValue(COMMERCIAL, "myTestCount", traceCount);
// Service flow...
```


## traceByValue

```TypeScript
function traceByValue(level: HiTraceOutputLevel, name: string, count: number): void
```

Traces an integer with the trace output level specified. It is used to mark the name and value of a predefined integer variable to be traced.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| level | [HiTraceOutputLevel](arkts-performanceanalysis-hitracemeter-hitraceoutputlevel-e.md) | Yes | Trace output level. |
| name | string | Yes | Name of the integer variable to trace. The maximum length of a trace record is 512 bytes. The excess part will be truncated. It is recommended that the length of this parameter be less than or equal to 420 bytes. |
| count | number | Yes | Value of an integer variable. |

**Examples**

See [traceByValue](#tracebyvalue)
