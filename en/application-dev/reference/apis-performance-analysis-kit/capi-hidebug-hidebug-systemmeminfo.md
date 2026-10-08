# HiDebug_SystemMemInfo

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=e927796ba68acb42b31a64400ef3f800e94a271e translatedAt=2026-09-21T02:32:11.220Z pushedAt=2026-09-22T01:29:30.382Z -->

```c
typedef struct HiDebug_SystemMemInfo {...} HiDebug_SystemMemInfo
```

## Overview

Defines the system memory information structure type. It is used to obtain key information such as the total, free, and available system memory, and is applicable to scenarios such as system performance analysis, memory monitoring, and fault diagnosis, helping developers understand system memory usage and optimize memory management strategies.

**Since**: 12

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t totalMem | Total memory of the system, in KB.|
| uint32_t freeMem | Free memory of the system, in KB.|
| uint32_t availableMem | Available memory of the system, in KB.|


