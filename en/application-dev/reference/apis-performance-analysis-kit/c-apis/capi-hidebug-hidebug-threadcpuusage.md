# HiDebug_ThreadCpuUsage

```c
typedef struct HiDebug_ThreadCpuUsage {...} HiDebug_ThreadCpuUsage
```

## Overview

Defines the struct for the CPU usage of all threads of an application.

<!--Device-struct HiDebug_ThreadCpuUsage {...}--><!--Device-struct HiDebug_ThreadCpuUsage {...}-End-->

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Related module**: [HiDebug](capi-performance-analysis-kit-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t threadId | Thread ID. |
| double cpuUsage | Thread CPU usage, in percentage. |
| [struct HiDebug_ThreadCpuUsage](capi-hidebug-hidebug-threadcpuusage.md) *next | Pointer to the CPU usage of the next thread. |


