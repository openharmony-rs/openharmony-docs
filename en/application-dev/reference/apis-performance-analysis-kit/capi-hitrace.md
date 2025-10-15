# HiTrace

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @qq_437963121-->
<!--Designer: @kutcherzhou1; @MontSaintMichel-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

HiTraceMeter provides APIs for system performance tracing.

You can call the APIs provided by HiTraceMeter in your own service logic to effectively track service processes and check the system performance.

HiTraceChain provides cross-thread and cross-process distributed tracing capabilities.

HiTraceChain can generate and transfer a unique trace ID in the service execution process. The trace ID is recorded in various debugging information (including HiTraceMeter dotting, application events, and HiLog logs) output in the service process. During debugging and fault locating, you can use the unique chain ID to quickly correlate various information related to the service process.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10
## Files

| Name| Description|
| -- | -- |
| [trace.h](capi-trace-h.md) | Defines APIs of the HiTraceMeter and HiTraceChain modules for performance trace and distributed tracing.<br>The vertical bar (|) is used as the separator in user-mode trace format. Therefore, the string parameters passed by the HiTraceMeter APIs must exclude this character to avoid trace parsing exceptions.<br>The maximum length of a user-mode trace is 512 characters. Excess characters will be truncated.|
