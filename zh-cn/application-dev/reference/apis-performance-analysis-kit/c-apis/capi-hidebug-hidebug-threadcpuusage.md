# HiDebug_ThreadCpuUsage

```c
typedef struct HiDebug_ThreadCpuUsage {...} HiDebug_ThreadCpuUsage
```

## 概述

Defines the struct for the CPU usage of all threads of an application.

**起始版本：** 12

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t threadId | Thread ID. |
| double cpuUsage | Thread CPU usage, in percentage. |
| struct [HiDebug_ThreadCpuUsage](capi-hidebug-hidebug-threadcpuusage.md) *next | Pointer to the CPU usage of the next thread. |


