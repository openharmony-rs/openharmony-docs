# HiTraceId

```c
struct HiTraceId {...}
```

## Overview

Defines a **HiTraceId** instance.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Since**: 12

**Related module**: [HiTrace](capi-others-hitrace.md)

**Header file**: [trace.h](capi-trace-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t valid : 1 | Whether a **HiTraceId** instance is valid.<br>**Since**: 12 |
| uint64_t ver : 3 | Version number of **HiTraceId**.<br>**Since**: 12 |
| uint64_t chainId : 60 | Trace chain ID of **HiTraceId**.<br>**Since**: 12 |
| uint64_t flags : 12 | Trace flag of **HiTraceId**.<br>**Since**: 12 |
| uint64_t spanId : 26 | Span ID of **HiTraceId**.<br>**Since**: 12 |
| uint64_t parentSpanId : 26 | Parent span ID of **HiTraceId**.<br>**Since**: 12 |
| uint64_t chainId : 60 | Trace chain ID of **HiTraceId**.<br>**Since**: 12 |
| uint64_t ver : 3 | Version number of **HiTraceId**.<br>**Since**: 12 |
| uint64_t valid : 1 | Whether a **HiTraceId** instance is valid.<br>**Since**: 12 |
| uint64_t parentSpanId : 26 | Parent span ID of **HiTraceId**.<br>**Since**: 12 |
| uint64_t spanId : 26 | Span ID of **HiTraceId**.<br>**Since**: 12 |
| uint64_t flags : 12 | Trace flag of **HiTraceId**.<br>**Since**: 12 |


