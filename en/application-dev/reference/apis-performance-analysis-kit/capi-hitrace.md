# HiTrace

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @yu_haoqiaida-->
<!--Designer: @MontSaintMichel-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=ddc44e45ef41553fe2aedd0159d6211134a3c798 translatedAt=2026-09-16T10:57:48.248Z pushedAt=2026-09-20T09:01:52.260Z -->

## Overview

**HiTraceMeter** provides system performance tracing APIs for developers.<br> By calling the **HiTraceMeter** APIs at key points in the service logic, developers can effectively measure the time consumed by critical execution flows and locate issues. It is suitable for scenarios where application performance bottlenecks need to be analyzed and the execution efficiency of critical paths needs to be optimized, helping developers quickly locate performance issues and optimize system performance.<br> **HiTraceChain** provides cross-thread and cross-process distributed tracing capabilities for developers.<br> **HiTraceChain** supports generating and passing a unique trace identifier during service execution, and recording this trace identifier in various types of debugging information output during the service flow (including **HiTraceMeter** tracing points, application events, and **hilog** logs). The unique trace identifier is a trace ID passed across threads and processes, used to correlate all debugging information of the same service flow. During debugging and issue locating, developers can use this identifier to quickly correlate all end-to-end information of the current service flow. It is suitable for scenarios such as distributed applications and microservice architectures that require tracing cross-service call chains, helping developers quickly locate cross-service faults and improve troubleshooting efficiency.<br>

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 10
## Files

| Name| Description|
| -- | -- |
| [trace.h](capi-trace-h.md) | Defines the APIs of the **HiTraceMeter** and **HiTraceChain** modules, which implement performance tracing and distributed tracing. These APIs support scenarios such as application performance analysis, cross-service call chain tracing, and performance bottleneck locating. They resolve the difficulties of tracing call chains and locating performance issues in distributed systems, improving system observability and troubleshooting efficiency. Performance tracing records function execution time by inserting markers at key code locations. Distributed tracing traces call chains across threads, processes, and devices through **HiTraceId**.<br> The user-mode trace format uses the vertical bar character as a delimiter. Therefore, string parameters passed through the **HiTraceMeter** API should avoid containing this character to prevent trace parsing exceptions.<br> The total length of a user-mode trace is limited to 512 characters, and any excess is truncated. |
