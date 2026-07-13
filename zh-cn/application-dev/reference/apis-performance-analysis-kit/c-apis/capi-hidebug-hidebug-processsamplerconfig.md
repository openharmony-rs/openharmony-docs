# HiDebug_ProcessSamplerConfig

```c
typedef struct HiDebug_ProcessSamplerConfig {...} HiDebug_ProcessSamplerConfig
```

## 概述

Defines a struct for sampling configuration.

**起始版本：** 22

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t* tids | Array of thread IDs to sample. A maximum of 10 threads can be sampled at the same time. If the array lengthexceeds 10, the first 10 threads are sampled. |
| uint32_t size | Length of the array to which **tids** points. |
| uint32_t frequency | Sampling frequency, in Hz. The value ranges from 1 to 200. If the value is out of the range, the default value 100** is used. |
| uint32_t duration | Sampling duration, in ms. The value ranges from 1000 to 10000. If the value is less than 1000, the API call isabnormal. If the value is greater than 10000, 10000 is used. |
| uint32_t reserved | Reserved. |


