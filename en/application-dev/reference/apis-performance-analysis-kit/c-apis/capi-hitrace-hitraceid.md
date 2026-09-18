# HiTraceId

```c
typedef struct HiTraceId {...} HiTraceId
```

## Overview

Defines a **HiTraceId** instance.

**Since**: 12

**Related module**: [HiTrace](capi-hitrace.md)

**Header file**: [trace.h](capi-trace-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t valid : 1 |  |
| uint64_t ver : 3 |  |
| uint64_t chainId : 60 |  |
| uint64_t flags : 12 |  |
| uint64_t spanId : 26 |  |
| uint64_t parentSpanId : 26;
#elif \_\_BYTE_ORDER == \_\_BIG_ENDIAN |  |
| uint64_t chainId : 60 |  |
| uint64_t ver : 3 |  |
| uint64_t valid : 1 |  |
| uint64_t parentSpanId : 26 |  |
| uint64_t spanId : 26 |  |
| uint64_t flags : 12;
#else
#error "ERROR: No BIG_LITTLE_ENDIAN defines."
#endif |  |


