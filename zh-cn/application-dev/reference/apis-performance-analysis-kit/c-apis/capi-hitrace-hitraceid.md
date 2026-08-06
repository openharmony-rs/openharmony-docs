# HiTraceId

```c
typedef struct HiTraceId {...} HiTraceId
```

## 概述

用于标识调用链的结构体。

**起始版本：** 12

**相关模块：** [HiTrace](capi-hitrace.md)

**所在头文件：** [trace.h](capi-trace-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t valid : 1 |  |
| uint64_t ver : 3 |  |
| uint64_t chainId : 60 |  |
| uint64_t flags : 12 |  |
| uint64_t spanId : 26 |  |
| uint64_t parentSpanId : 26;
#elif __BYTE_ORDER == __BIG_ENDIAN |  |
| uint64_t chainId : 60 |  |
| uint64_t ver : 3 |  |
| uint64_t valid : 1 |  |
| uint64_t parentSpanId : 26 |  |
| uint64_t spanId : 26 |  |
| uint64_t flags : 12;
#else
#error "ERROR: No BIG_LITTLE_ENDIAN defines."
#endif |  |


