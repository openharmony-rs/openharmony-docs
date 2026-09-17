# @ohos.hiTraceChain(Distributed Tracing)

The **hiTraceChain** module implements call chain trace throughout a service process. It provides functions such as starting and stopping call chain trace and configuring trace points.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

## Modules to Import

```TypeScript
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [begin](arkts-performanceanalysis-hitracechain-begin-f.md) | Starts call chain trace. This API returns the result synchronously. |
| [clearId](arkts-performanceanalysis-hitracechain-clearid-f.md) | Clears the trace ID. This API returns the result synchronously. |
| [createSpan](arkts-performanceanalysis-hitracechain-createspan-f.md) | Creates a trace span. This API works in synchronous manner. |
| [enableFlag](arkts-performanceanalysis-hitracechain-enableflag-f.md) | Enables the trace flag specified in HiTraceId. This API returns the result synchronously. |
| [end](arkts-performanceanalysis-hitracechain-end-f.md) | Stops call chain trace. This API works in synchronous manner. |
| [getId](arkts-performanceanalysis-hitracechain-getid-f.md) | Obtains the trace ID. This API returns the result synchronously. |
| [isFlagEnabled](arkts-performanceanalysis-hitracechain-isflagenabled-f.md) | Checks whether the trace flag is enabled for **HiTraceId**. This API returns the result synchronously. |
| [isValid](arkts-performanceanalysis-hitracechain-isvalid-f.md) | Checks whether a **HiTraceId** instance is valid. This API returns the result synchronously. |
| [setId](arkts-performanceanalysis-hitracechain-setid-f.md) | Sets a trace ID. This API returns the result synchronously. |
| [tracepoint](arkts-performanceanalysis-hitracechain-tracepoint-f.md) | Adds a trace point for the [@ohos.hiTraceMeter (Performance Tracing)](arkts-performanceanalysis-hitracemeter.md) logging, which is synchronous. |

### Interfaces

| Name | Description |
| --- | --- |
| [HiTraceId](arkts-performanceanalysis-hitracechain-hitraceid-i.md) | Defines a **HiTraceId** object. |

### Enums

| Name | Description |
| --- | --- |
| [HiTraceCommunicationMode](arkts-performanceanalysis-hitracechain-hitracecommunicationmode-e.md) | Enumerates communication modes. |
| [HiTraceFlag](arkts-performanceanalysis-hitracechain-hitraceflag-e.md) | Enumerates trace flag types. |
| [HiTraceTracepointType](arkts-performanceanalysis-hitracechain-hitracetracepointtype-e.md) | Enumerates trace point types. |
