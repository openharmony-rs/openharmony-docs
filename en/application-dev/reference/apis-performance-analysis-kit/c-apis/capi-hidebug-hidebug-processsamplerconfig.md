# HiDebug_ProcessSamplerConfig

```c
typedef struct HiDebug_ProcessSamplerConfig {...} HiDebug_ProcessSamplerConfig
```

## Overview

Defines a struct for sampling configuration.

<!--Device-struct HiDebug_ProcessSamplerConfig {...}--><!--Device-struct HiDebug_ProcessSamplerConfig {...}-End-->

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 22

**Related module**: [HiDebug](capi-performance-analysis-kit-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t* tids | Array of thread IDs to sample. A maximum of 10 threads can be sampled at the same time. If the array length exceeds 10, the first 10 threads are sampled.<br><!--Device-uint32_t* tids--><!--Device-uint32_t* tids-End--> |
| uint32_t size | Length of the array to which **tids** points.<br><!--Device-uint32_t size--><!--Device-uint32_t size-End--> |
| uint32_t frequency | Sampling frequency, in Hz. The value ranges from 1 to 200. If the value is out of the range, the default value ** 100** is used.<br><!--Device-uint32_t frequency--><!--Device-uint32_t frequency-End--> |
| uint32_t duration | Sampling duration, in ms. The value ranges from 1000 to 10000. If the value is less than 1000, the API call is abnormal. If the value is greater than 10000, 10000 is used.<br><!--Device-uint32_t duration--><!--Device-uint32_t duration-End--> |
| uint32_t reserved | Reserved.<br><!--Device-uint32_t reserved--><!--Device-uint32_t reserved-End--> |


