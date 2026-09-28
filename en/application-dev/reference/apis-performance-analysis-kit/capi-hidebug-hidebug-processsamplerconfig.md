# HiDebug_ProcessSamplerConfig

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=d887f892bc8a14c269d1d611c88c0769836d883f translatedAt=2026-09-21T02:31:13.187Z pushedAt=2026-09-22T01:29:30.380Z -->

```c
typedef struct HiDebug_ProcessSamplerConfig {...} HiDebug_ProcessSamplerConfig
```

## Overview

Defines the sampling configuration.

**Since**: 22

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t* tids | Array of thread IDs to sample. A maximum of 10 threads can be sampled at the same time. If the array length exceeds 10, the first 10 threads are sampled.|
| uint32_t size | Length of the array pointed to by `tids`. This value must be consistent with the actual length of the `tids` array. |
| uint32_t frequency | Sampling frequency, with a value range of [1-200] in Hz. If the value is out of range, the default value **100** is used. |
| uint32_t duration | Sampling duration, in ms. The value ranges from 1000 to 10000. If the value is less than 1000, the API call is abnormal. If the value is greater than 10000, 10000 is used.|
| uint32_t reserved | Reserved.|


