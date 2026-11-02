# HiTraceId

```c
struct HiTraceId {...}
```

## 概述

用于标识调用链的结构体。

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**起始版本：** 12

**相关模块：** [HiTrace](capi-others-hitrace.md)

**所在头文件：** [trace.h](capi-trace-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t valid : 1 | HiTraceId是否有效，1表示有效，0表示无效。用于判断HiTraceId结构体是否包含有效的跟踪信息。<br>**起始版本：** 12 |
| uint64_t ver : 3 | HiTraceId的版本号，用于表示HiTraceId结构体的版本。不同版本可能有不同的字段布局或功能特性。<br>**起始版本：** 12 |
| uint64_t chainId : 60 | HiTraceId的跟踪链标识，用于唯一标识跨进程/跨设备的调用链。在整个分布式跟踪过程中保持不变，用于关联同一业务流程的所有跟踪信息。<br>**起始版本：** 12 |
| uint64_t flags : 12 | HiTraceId的跟踪标识位，用于指定跟踪选项或特性。不同的标志位组合可以控制跟踪的详细程度和行为。<br>**起始版本：** 12 |
| uint64_t spanId : 26 | HiTraceId的分支标识，用于标识调用链中的当前调用节点。每次创建新的分支时会产生新的spanId，用于构建调用树结构。<br>**起始版本：** 12 |
| uint64_t parentSpanId : 26 | HiTraceId的父分支标识，用于标识调用链中当前节点的父节点。通过parentSpanId可以追溯调用的来源，实现调用链的层级关系。<br>**起始版本：** 12 |
| uint64_t chainId : 60 | HiTraceId的跟踪链标识，用于唯一标识跨进程/跨设备的调用链。在整个分布式跟踪过程中保持不变，用于关联同一业务流程的所有跟踪信息。<br>**起始版本：** 12 |
| uint64_t ver : 3 | HiTraceId的版本号，用于表示HiTraceId结构体的版本。不同版本可能有不同的字段布局或功能特性。<br>**起始版本：** 12 |
| uint64_t valid : 1 | HiTraceId是否有效，1表示有效，0表示无效。用于判断HiTraceId结构体是否包含有效的跟踪信息。<br>**起始版本：** 12 |
| uint64_t parentSpanId : 26 | HiTraceId的父分支标识，用于标识调用链中当前节点的父节点。通过parentSpanId可以追溯调用的来源，实现调用链的层级关系。<br>**起始版本：** 12 |
| uint64_t spanId : 26 | HiTraceId的分支标识，用于标识调用链中的当前调用节点。每次创建新的分支时会产生新的spanId，用于构建调用树结构。<br>**起始版本：** 12 |
| uint64_t flags : 12 | HiTraceId的跟踪标识位，用于指定跟踪选项或特性。不同的标志位组合可以控制跟踪的详细程度和行为。<br>**起始版本：** 12 |


