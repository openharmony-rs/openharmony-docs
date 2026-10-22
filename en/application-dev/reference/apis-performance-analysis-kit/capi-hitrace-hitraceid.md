# HiTraceId

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @yu_haoqiaida-->
<!--Designer: @MontSaintMichel-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=0e8943e8b8dd159f54837747c5c7d06207b95bd2 translatedAt=2026-09-16T10:56:22.898Z pushedAt=2026-09-20T09:01:52.258Z -->

```c
typedef struct HiTraceId {...} HiTraceId
```

## Overview

Defines a struct used to identify the call chain.

When to use:
- Cross-service call tracing: In a distributed system, **HiTraceId** is used to identify and correlate the call chain of the same service request across different services.
- Performance analysis: Works with the HiTrace call chain tracing feature to analyze application performance bottlenecks and call latency.
- Log correlation: In the logging system, **HiTraceId** correlates logs from different phases of the same request to facilitate troubleshooting.
- Call chain visualization: **HiTraceId** enables end-to-end call chain visualization, helping to understand system behavior.

**Since**: 12

**Related module**: [HiTrace](capi-hitrace.md)

**Header file**: [trace.h](capi-trace-h.md)

## Summary

### Member Variables

A little-endian **HiTraceId** consists of the following fields in sequence: 

| Field| Number of Bits| Description|
| -------- | -------- | -------- |
| uint64_t valid | 1 | Whether **HiTraceId** is valid. **1** indicates valid, and **0** indicates invalid. It is used to determine whether the **HiTraceId** structure contains valid trace information. |
| uint64_t ver | 3 | Version number of **HiTraceId**, used to identify the version of the **HiTraceId** structure. Different versions may have different field layouts or functional features. |
| uint64_t chainId | 60 | Trace chain identifier of **HiTraceId**, used to uniquely identify a cross-process/cross-device call chain. It remains unchanged throughout the distributed tracing process and is used to correlate all trace information of the same business process. |
| uint64_t flags | 12 | Trace flag bits of **HiTraceId**, used to specify tracing options or features. Different flag bit combinations can control the detail level and behavior of tracing. |
| uint64_t spanId | 26 | Span ID of **HiTraceId**, used to identify the current call node in the call chain. A new **spanId** is generated each time a new branch is created, and it is used to build the call tree structure. |
| uint64_t parentSpanId | 26 | Parent span ID of **HiTraceId**, used to identify the parent node of the current node in the call chain. The call source can be traced through **parentSpanId** to implement the hierarchical relationship of the call chain. |

A big-endian **HiTraceId** consists of the following fields in sequence:

| Field| Number of Bits| Description|
| -------- | -------- | -------- |
| uint64_t chainId | 60 | Trace chain ID of **HiTraceId**, used to identify the call chain across processes/devices. It remains unchanged throughout the distributed tracing process and is used to associate all tracing information of the same business process. |
| uint64_t ver | 3 | Version number of **HiTraceId**, used to identify the version of the **HiTraceId** structure. Different versions may have different field layouts or functional features. |
| uint64_t valid | 1 | Whether **HiTraceId** is valid. 1 indicates valid, and 0 indicates invalid. It is used to determine whether the **HiTraceId** structure contains valid tracing information. |
| uint64_t parentSpanId | 26 | Parent span ID of **HiTraceId**, used to identify the parent node of the current node in the call chain. The source of a call can be traced through **parentSpanId** to implement the hierarchical relationship of the call chain. |
| uint64_t spanId | 26 | Span ID of **HiTraceId**, used to identify the current call node in the call chain. A new **spanId** is generated each time a new span is created, and it is used to build the call tree structure. |
| uint64_t flags | 12 | Tracing flag bits of **HiTraceId**, used to specify tracing options or features. Different flag bit combinations can control the detail level and behavior of tracing. |



