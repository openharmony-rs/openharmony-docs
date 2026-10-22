# @ohos.hiTraceChain(Distributed Tracing)

The **hiTraceChain** module implements call chain trace throughout a service process. It provides functions such as starting and stopping call chain trace and configuring trace points.

**Since:** 8

<!--Device-unnamed-declare namespace hiTraceChain--><!--Device-unnamed-declare namespace hiTraceChain-End-->

**System capability:** SystemCapability.HiviewDFX.HiTrace

## Modules to Import

```TypeScript
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [begin](arkts-performanceanalysis-hitracechain-begin-f.md#begin-1) | Starts call chain trace. This API returns the result synchronously. |
| [clearId](arkts-performanceanalysis-hitracechain-clearid-f.md#clearid-1) | Clears the trace ID. This API returns the result synchronously. |
| [createSpan](arkts-performanceanalysis-hitracechain-createspan-f.md#createspan-1) | Creates a trace span. This API works in synchronous manner. |
| [enableFlag](arkts-performanceanalysis-hitracechain-enableflag-f.md#enableflag-1) | Enables the trace flag specified in HiTraceId. This API returns the result synchronously. |
| [end](arkts-performanceanalysis-hitracechain-end-f.md#end-1) | Stops call chain trace. This API works in synchronous manner. |
| [getId](arkts-performanceanalysis-hitracechain-getid-f.md#getid-1) | Obtains the trace ID. This API returns the result synchronously. |
| [isFlagEnabled](arkts-performanceanalysis-hitracechain-isflagenabled-f.md#isflagenabled-1) | Checks whether the trace flag is enabled for **HiTraceId**. This API returns the result synchronously. |
| [isValid](arkts-performanceanalysis-hitracechain-isvalid-f.md#isvalid-1) | Checks whether a **HiTraceId** instance is valid. This API returns the result synchronously. |
| [setId](arkts-performanceanalysis-hitracechain-setid-f.md#setid-1) | Sets a trace ID. This API returns the result synchronously. |
| [tracepoint](arkts-performanceanalysis-hitracechain-tracepoint-f.md#tracepoint-1) | Adds a trace point for the [@ohos.hiTraceMeter (Performance Tracing)](arkts-performanceanalysis-hitracemeter.md) logging, which is synchronous. |

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
