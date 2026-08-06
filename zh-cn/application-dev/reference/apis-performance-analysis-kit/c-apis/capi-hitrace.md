# HiTrace

## 概述

hitraceChain provides APIs for cross-thread and cross-process distributed tracing.hiTraceChain generates a unique chain ID for a service process and passes it to various information (includingapplication events, system events, and logs) specific to the service process.During debugging and fault locating, you can use the unique chain ID to quickly correlate various informationrelated to the service process.

**起始版本：** 10
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [trace.h](capi-trace-h.md) | HiTraceMeter和HiTraceChain模块接口定义，通过这些接口实现性能打点和分布式跟踪功能。支持应用性能分析、跨服务调用链追踪、性能瓶颈定位、等场景，能够解决分布式系统中调用链路难以追踪、性能问题难以定位的问题，提升系统可观测性和问题排查效率。性能打点通过在代码关键位置插入标记，记录函数执行时间；分布式跟踪通过HiTraceId实现跨线程、跨进程、跨设备的调用链追踪。 |
