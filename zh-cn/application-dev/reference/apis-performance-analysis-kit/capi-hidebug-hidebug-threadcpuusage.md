# HiDebug_ThreadCpuUsage

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct HiDebug_ThreadCpuUsage {...} HiDebug_ThreadCpuUsage
```

## 概述

当前进程所有线程的CPU使用率结构体定义。

使用场景：

应用性能监控：获取线程CPU使用率，监控应用的运行状态和性能瓶颈。

线程性能优化：分析各线程的CPU占用情况，优化线程调度和资源分配。

系统调试：在调试阶段追踪线程的CPU使用情况，定位性能问题。

**起始版本：** 12

**相关模块：** [HiDebug](capi-hidebug.md)

**所在头文件：** [hidebug_type.h](capi-hidebug-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t threadId | 线程ID。 |
| double cpuUsage | 线程CPU使用率百分比。 |
| struct [HiDebug_ThreadCpuUsage](capi-hidebug-hidebug-threadcpuusage.md) *next | 下一个线程的使用率信息。 |


