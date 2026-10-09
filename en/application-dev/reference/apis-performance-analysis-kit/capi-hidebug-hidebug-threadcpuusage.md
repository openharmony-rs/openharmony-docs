# HiDebug_ThreadCpuUsage

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=00ffa17dad78f74cc2e0acc571993c663e969c2a translatedAt=2026-09-16T10:46:55.605Z pushedAt=2026-09-20T09:01:52.248Z -->

```c
typedef struct HiDebug_ThreadCpuUsage {...} HiDebug_ThreadCpuUsage
```

## Overview

Defines the struct for the CPU usage of all threads of the current process.

When to use:

Application performance monitoring: Obtain thread CPU usage to monitor the running status and performance bottlenecks of an application.

Thread performance optimization: Analyze the CPU usage of each thread to optimize thread scheduling and resource allocation.

System debugging: Track thread CPU usage during debugging to locate performance issues.

**Since**: 12

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t threadId | Thread ID.|
| double cpuUsage | Thread CPU usage, in percentage.|
| struct [HiDebug_ThreadCpuUsage](capi-hidebug-hidebug-threadcpuusage.md) *next | Pointer to the CPU usage of the next thread.|


