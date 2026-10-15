# @ohos.hiTraceMeter(Performance Tracing)

The **HiTraceMeter** module provides the functions of tracing service processes and monitoring the system performance. It provides the data needed for HiTraceMeter to carry out performance analysis.

For details about the development process, see [Using HiTraceMeter (ArkTS)](../../../dfx/hitracemeter-guidelines-arkts.md).

> **NOTE:** 
> 
> You are advised to use the performance tracing APIs of API version 19. The
> [startTrace()](arkts-performanceanalysis-hitracemeter-starttrace-f.md), [finishTrace()](arkts-performanceanalysis-hitracemeter-finishtrace-f.md), and
> [traceByValue()](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md) APIs will be deprecated.
> 
> The trace output level cannot be specified in the [startTrace()](arkts-performanceanalysis-hitracemeter-starttrace-f.md),
> [finishTrace()](arkts-performanceanalysis-hitracemeter-finishtrace-f.md) and [traceByValue()](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md) APIs. By
> default, the trace output level is **COMMERCIAL**.
> 
> The vertical bar (|) is used as the separator in
> [user-mode trace format](../../../dfx/hitracemeter-view.md#user-mode-trace-format). Therefore, the string
> parameters passed by the performance tracing APIs must exclude this character to avoid trace parsing exceptions.
> 
> The maximum length of a [user-mode trace](../../../dfx/hitracemeter-view.md#user-mode-trace-format) is 512
> characters. Excess characters will be truncated.

**Since:** 8

<!--Device-unnamed-declare namespace hiTraceMeter--><!--Device-unnamed-declare namespace hiTraceMeter-End-->

**System capability:** SystemCapability.HiviewDFX.HiTrace

## Modules to Import

```TypeScript
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [finishAsyncTrace](arkts-performanceanalysis-hitracemeter-finishasynctrace-f.md#finishasynctrace) | Stops an asynchronous trace with the trace output level specified. |
| [finishSyncTrace](arkts-performanceanalysis-hitracemeter-finishsynctrace-f.md#finishsynctrace) | Stops a synchronous trace with the trace output level specified. |
| [finishTrace](arkts-performanceanalysis-hitracemeter-finishtrace-f.md#finishtrace) | Stops an asynchronous trace. |
| [isTraceEnabled](arkts-performanceanalysis-hitracemeter-istraceenabled-f.md#istraceenabled) | Checks whether application trace capture is enabled. |
| [registerTraceListener](arkts-performanceanalysis-hitracemeter-registertracelistener-f.md#registertracelistener) | Registers a callback to notify whether the application trace capture is enabled. This API uses an asynchronous callback to return the result. |
| [startAsyncTrace](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md#startasynctrace) | Starts an asynchronous trace with the trace output level specified. |
| [startSyncTrace](arkts-performanceanalysis-hitracemeter-startsynctrace-f.md#startsynctrace) | Starts a synchronous trace with the trace output level specified. For details, see [finishSyncTrace()](arkts-performanceanalysis-hitracemeter-finishsynctrace-f.md). |
| [startTrace](arkts-performanceanalysis-hitracemeter-starttrace-f.md#starttrace) | Starts an asynchronous trace. |
| [traceByValue](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md#tracebyvalue1) | Traces the value changes of an integer variable. |
| [traceByValue](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md#tracebyvalue2) | Traces an integer with the trace output level specified. It is used to mark the name and value of a predefined integer variable to be traced. |
| [unregisterTraceListener](arkts-performanceanalysis-hitracemeter-unregistertracelistener-f.md#unregistertracelistener) | Unregisters the callback function used to notify whether the trace capture is enabled, which is registered using **registerTraceListener()**. |

### Types

| Name | Description |
| --- | --- |
| [TraceEventListener](arkts-performanceanalysis-hitracemeter-traceeventlistener-t.md) | Defines a callback to listen for whether the trace capture is enabled. |

### Enums

| Name | Description |
| --- | --- |
| [HiTraceOutputLevel](arkts-performanceanalysis-hitracemeter-hitraceoutputlevel-e.md) | Enumerates trace output levels. |
