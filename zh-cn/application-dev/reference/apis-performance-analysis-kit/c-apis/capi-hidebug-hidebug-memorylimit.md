# HiDebug_MemoryLimit

```c
typedef struct HiDebug_MemoryLimit {...} HiDebug_MemoryLimit
```

## 概述

Defines the struct for the memory limit of the application process.

**起始版本：** 12

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t rssLimit | Limit on the physical memory size of the application process, in KB. Currently, the system does not limit thephysical memory size of the process. However, the available physical memory of the process cannot exceed themaximum physical memory of the device. You can call {@link OH_HiDebug_GetSystemMemInfo} to obtain the physicalmemory usage of the device. |
| uint64_t vssLimit | Limit on the virtual set size, in KB. |


