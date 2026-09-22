# OH_HiDebug_ResProfilerConfig

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=e927796ba68acb42b31a64400ef3f800e94a271e translatedAt=2026-09-21T02:33:21.997Z pushedAt=2026-09-22T01:29:30.387Z -->

```c
typedef struct OH_HiDebug_ResProfilerConfig {...} OH_HiDebug_ResProfilerConfig
```

## Overview

Defines a struct for the resource collection configurations.

**Since**: 24

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t maxDuration | Maximum collection duration, in seconds. The value range is [1, 3600].<br>If the value of the input parameter is out of the value range, the API returns the error code [HIDEBUG_RES_PROF_INVALID_MAX_DURATION](capi-hidebug-type-h.md#hidebug_errorcode).<br> **Since**: 24|
| uint32_t filterSize | Filter size, in bytes. The value range is [1, 4294967295].<br>If the value of the input parameter is out of the value range, the API returns the error code [HIDEBUG_RES_PROF_INVALID_FILTER_SIZE](capi-hidebug-type-h.md#hidebug_errorcode).<br> **Since**: 24|
| uint32_t maxStackDepth | Maximum stack trace depth, with a value range of [0, 30], in frames. It is recommended to set an appropriate stack depth based on actual requirements. A greater depth incurs higher collection overhead.<br>If the input parameter is out of range, the API returns error code [HIDEBUG_RES_PROF_INVALID_MAX_STACK_DEPTH](capi-hidebug-type-h.md#hidebug_errorcode).<br> **Since**: 24 |
| uint32_t statisticsInterval | Statistical interval, in seconds. The value range is [0, 3600].<br>If the value of the input parameter is out of the value range, the API returns the error code [HIDEBUG_RES_PROF_INVALID_STATISTICS_INTERVAL](capi-hidebug-type-h.md#hidebug_errorcode).<br> **Since**: 24|
| uint32_t sampleInterval | Sampling size, in bytes. The value range is [384, 4294967295].<br>In sampling mode, if the allocated memory size is less than or equal to the sampling size, probabilistic sampling is performed. Otherwise, full sampling is performed.<br>If the value of the input parameter is out of the range, the API returns the error code [HIDEBUG_RES_PROF_INVALID_SAMPLE_INTERVAL](capi-hidebug-type-h.md#hidebug_errorcode).<br> **Since**: 24|

